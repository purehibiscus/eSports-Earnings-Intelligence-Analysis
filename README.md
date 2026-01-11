# eSports-Game-2015-2024-Trend-Analysis

**Esports Earnings Intelligence Analysis**


Tools: Power BI, Excel, VS Code, Kaggle CSVs
Domain: Global Esports Economics & Market Intelligence

**Executive Summary**

This project delivers an end-to-end Business Intelligence solution analyzing global esports earnings across players, teams, games, genres, and geographies between 2015 and 2024.
The objective was to transform raw, inconsistent Kaggle datasets into a clean, modeled, executive-ready analytics platform that supports:
  - Strategic decision-making
  - Market expansion analysis
  - Performance benchmarking
  - Prize pool concentration risk assessment

**Business Scenario & Problem Statement**


**Business Need**

The Esports World Cup Foundation requires a centralized intelligence layer to answer questions such as:
  - Where is prize money concentrated?
  - Which regions, games, and teams dominate earnings?
  - How balanced is the esports economy?
  - Which markets present growth or diversification opportunities?

**Constraints**

- Source data lacked transactional timestamps
- Player names contained encoding corruption
- Country–continent relationships were ambiguous
- Earnings data was highly skewed


**Data Sources**

All datasets were sourced from Kaggle and ingested as CSV files:
1. Country & Continent Reference Table
  - Continent_Name
  - Continent_Code
  - Country_Name
  - Two_Letter_Country_Code
  - Three_Letter_Country_Code
  - Country_Number
2. Highest Earning Players
  - PlayerId
  - First Name
  - Last Name
  - Current Handle
  - Country Code
  - Total Prize (USD)
  - Game
  - Genre
3. Highest Earning Teams
  - TeamId
  - TeamName
  - TotalUSDPrize
  - TotalTournaments
  - Game
  - Genre

**Data Cleaning & Quality Framework**

Non-Printable Character Issue (Critical)

Several player names contained corrupted characters such as:

- è½»é›¨
- Äá»©c Chiáº¿n

**3-Step Best Practice Cleaning Framework**

**Step 1:** Identify Root Cause
  - Encoding corruption confirmed
  - Not legitimate non-Latin characters
**Step 2:** Validate Using Multiple Tools
  - Excel UTF-8 import: inconclusive
  - VS Code: revealed corrupted values
  - Cross-referenced against real player names
**Step 3:** Correct & Standardize
  - Manually corrected First Name, Last Name, Handle
  - Ensured UTF-8 consistency
  - Preserved semantic meaning

**Tools Used:**
  - Excel (initial inspection)
  - VS Code (source-of-truth validation)

**Additional Cleaning Actions**

  - Removed 3-letter country codes; standardized to 2-letter ISO
  - Uppercased country abbreviations
  - Corrected misspelled country names
  - Validated earnings (no missing values)
  - Accepted skewed distribution as business-realistic

**Synthetic Date Dimension (Benchmarking Justification)**

1. Why a Date Table Was Added

The source data represented aggregated lifetime earnings, not transactions.
Adding a synthetic Date dimension is standard BI practice when:

  - Trend analysis is required
  - Benchmarking is the goal
  - Assumptions are clearly documented

**Important:**

**This project explicitly treats time analysis as scenario & benchmarking, not transactional truth.
**

  - Date Table Design (BI-Standard)
  - Column	Description
  - Date	Calendar date
  - Date_Key	YYYYMMDD
  - Year	Calendar year
  - Quarter	Q1–Q4
  - MonthNumber	1–12
  - MonthName	January–December
  - YearMonth	YYYY-MM
  - WeekNumber	ISO week
  - Day	Day of month
  - DayName	Monday–Sunday
  - IsWeekend	TRUE / FALSE

**Data Modeling (Star Schema)**

**Dimensions**

  - dim_player
  - dim_team
  - dim_game
  - dim_country
  - dim_continent
  - dim_date

**Bridge Table**

  - bridge_country_continent
(Resolves Turkey-style Europe/Asia ambiguity)

**Fact Table**

**fact_player_team_earnings**
  - Player earnings
  - Team earnings
  - Snapshot date
  - Game, country, team keys
 
 **Design Principles**
  - No relationships between dimension tables
  - All filters flow from dimensions → fact
  - Surrogate keys used consistently


**Dashboards Created (Power BI)**


**Executive Overview Dashboard**

**KPIs**
  - Total Prize Pool: $398M
  - Total Teams: 505
  - Total Players: 998
  - Total Games: 10
  - Avg Prize per Player: $399K
  - Prize Concentration (Top Players): $170.82M

**Insights**
  - Prize spikes at weeks 9, 12, 18, 24, 33, 37, 39, 42, 44, 49, 52
  - End-of-year prize accumulation trend observed

**Player & Team Performance Dashboard**

**Insights**
  - Top 10 players average $5.5M
  - Lower quartile at $3.6M
  - Leading teams:
      - Enterprise Gaming: $34M
      - Swedish National Team: $33.1M
      - Isurus Gaming: $21.7M
      - San Francisco Shock: $17.2M

**Game & Genre Economics Dashboard**

**Insights**
  - Hearthstone leads with $179M (35%)
  - Fortnite: $39M
  - League of Legends: $35M
  - MOBA genre dominates participation (31 players)
  - Collectible Card Games lead prize pools

**Geography & Market Expansion Dashboard**

**Insights**
  - Top countries:
  - China: $72M
  - South Korea: $58M
  - USA: $43M
  - Weekday prize pools exceed weekends
  - Africa & Asia lead continents (~$118M)

**UI / UX & Color System**

  - Championship Gold → Financial metrics
  - Electric Cyan → Trends & momentum
  - Charcoal & Slate → Structure & hierarchy
  - Designed for executive consumption

**Key Recommendations**

1. Prize Concentration Risk
  - High concentration suggests dependency on elite players
  - Diversification strategies recommended

2. Regional Growth Focus
  - Africa & Asia show strong upside
  - Opportunity for localized tournaments

3. Genre Investment Strategy
  - Sustain MOBA dominance
  - Expand Battle Royale ecosystems

4. Calendar Optimization
  - Peak weeks should guide flagship events

**Skills Demonstrated**
	
  - Business intelligence architecture
  - Data quality frameworks
  - Power BI modeling & DAX
  - Executive storytelling
  - Benchmarking methodology
  - Esports industry understanding
