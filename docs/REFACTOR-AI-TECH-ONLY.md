# Refactor Plan: AI & Technology Only

**Goal:** Remove all sources and panels that do not pertain to AI or technology, so the app becomes a focused AI/tech monitor.

---

## 1. Summary

| Area | Keep (AI/tech) | Remove (non-AI/tech) |
|------|----------------|----------------------|
| **Panels** | Map, Live News (tech headlines), AI Insights, AI Strategic Posture*, Tech, AI/ML, Startups, VC, Security, Policy/Regulation, Hardware, Cloud, Dev, GitHub, Layoffs, Tech Events, Service Status, Tech Readiness, Monitors, Markets (tech stocks), Crypto, Polymarket (tech predictions), Macro signals, ETF/Stablecoins (optional) | Regional news (politics, us, europe, middleeast, africa, latam, asia), CII, Strategic Risk, Intel, GDELT Intel, Cascade, Energy, Gov, Think tanks, Commodities, Fires, UCDP, Giving, Displacement, Climate, Population Exposure, Happy variant panels, Finance-only panels |
| **Feeds** | tech, ai, startups, vcblogs, regionalStartups, security, policy, hardware, cloud, dev, github, layoffs, unicorns, accelerators, funding, producthunt, outages | politics, us, europe, middleeast, africa, latam, asia, energy, gov, thinktanks, crisis, finance (or narrow to tech finance), commodities, forex, bonds, centralbanks, economic, ipo (or keep for tech), derivatives, fintech, regulation (financial), institutional, gccNews, positive, science, nature, health, inspiring, INTEL_SOURCES (defense/geopolitical) |
| **Server/API** | news, research (HN, arxiv, tech events, trending repos), intelligence (only if used for AI briefs), cyber, infrastructure (outages, cables, service status), market (tech-relevant: stocks, crypto, predictions) | maritime, military, unrest, conflict, seismology, wildfire, displacement, climate, positive-events, giving, economic (FRED, energy prices, World Bank), aviation (delays), prediction (keep Polymarket tech only) |
| **Map layers** | cables, datacenters, cyberThreats, startupHubs, cloudRegions, techHQs, techEvents, outages, weather (optional) | conflicts, bases, pipelines, hotspots, ais, nuclear, irradiators, sanctions, waterways, economic, protests, flights, military, natural, spaceports, minerals, fires, ucdpEvents, displacement, climate, positiveEvents, kindness, happiness, speciesRecovery, renewableInstallations, tradeRoutes, stockExchanges, financialCenters, centralBanks, commodityHubs, gulfInvestments |

\* “AI Strategic Posture” in tech variant is about tech/theater posture; either keep (if it’s tech-focused) or remove if it’s military/vessel-based.

---

## 2. Panels – Keep vs Remove

### 2.1 Keep (AI / Technology)

- **map** – Global Tech Map
- **live-news** – Tech Headlines
- **live-webcams** – optional (can remove if not tech)
- **insights** – AI Insights
- **strategic-posture** – only if refactored to tech posture; else **remove**
- **tech** – Technology
- **ai** – AI/ML News
- **startups** – Startups & VC
- **vcblogs** – VC Insights
- **regionalStartups** – Global Startup News
- **unicorns** – Unicorn Tracker
- **accelerators** – Accelerators & Demo Days
- **security** – Cybersecurity
- **policy** – AI Policy & Regulation
- **regulation** – AI Regulation Dashboard
- **layoffs** – Layoffs Tracker
- **hardware** – Semiconductors & Hardware
- **cloud** – Cloud & Infrastructure
- **dev** – Developer Community
- **github** – GitHub Trending
- **ipo** – IPO & SPAC (tech IPOs)
- **funding** – Funding & VC
- **producthunt** – Product Hunt
- **events** – Tech Events
- **service-status** – Service Status
- **tech-readiness** – Tech Readiness Index
- **monitors** – My Monitors
- **markets** – Tech stocks only
- **finance** – Tech/finance headlines only (or merge into tech)
- **crypto** – Crypto
- **polymarket** – Tech Predictions
- **macro-signals** – Market Radar (optional)
- **etf-flows** / **stablecoins** – optional

### 2.2 Remove

- **cii** – Country Instability (geopolitical)
- **strategic-risk** – Strategic Risk Overview (geopolitical)
- **intel** – Intel Feed (defense/geopolitical)
- **gdelt-intel** – Live Intelligence (geopolitical)
- **cascade** – Infrastructure Cascade (keep only if limited to tech infra; else remove)
- **politics, us, europe, middleeast, africa, latam, asia** – Regional news
- **energy** – Energy & Resources (unless tech/energy)
- **gov** – Government (geopolitical)
- **thinktanks** – Think Tanks (geopolitical; or keep only tech think tanks)
- **commodities** – Commodities
- **heatmap** – Sector heatmap (optional; keep if tech sectors only)
- **satellite-fires** – Fires
- **ucdp-events** – UCDP Conflict Events
- **giving** – Global Giving
- **displacement** – UNHCR Displacement
- **climate** – Climate Anomalies
- **population-exposure** – Population Exposure
- **gcc-investments** – GCC Investments (finance variant)
- **positive-feed, progress, counters, spotlight, breakthroughs, digest, species, renewable** – Happy variant

---

## 3. Data Sources & Services – Keep vs Remove

### 3.1 Client-side services to KEEP

- `services/research` – HN, arxiv, tech events
- `services/tech-activity`, `services/geo-hub-index`, `services/startup-ecosystems` (or config)
- `services/infrastructure` – outages, cables, service status
- `services/threat-classifier` – if used for cyber; else trim
- `services/trending-keywords`, `services/sentiment-gate` (if used for tech news)
- `services/ai-flow-settings`, `services/runtime-config`
- Market/crypto/prediction clients used for tech stocks and crypto
- `services/clustering`, `services/ml-worker`, `services/analysis-worker` (AI insights)
- `services/desktop-readiness`, `services/tauri-bridge`
- Config: `tech-companies`, `ai-regulations`, `startup-ecosystems`, `ai-datacenters`, `tech-geo` (STARTUP_HUBS, ACCELERATORS, TECH_HQS, CLOUD_REGIONS)

### 3.2 Client-side services to REMOVE or trim

- `services/military`, `services/military-flights`, `services/cached-theater-posture`, `services/military-surge`
- `services/aviation` (unless for tech travel only)
- `services/conflict`, `services/displacement`, `services/climate`, `services/population-exposure`
- `services/unrest`, `services/gdacs`, `services/usa-spending`
- `services/conservation-data`, `services/renewable-energy-data`, `services/celebration`, `services/happiness-data`, `services/kindness-data`, `services/positive-events-geo`, `services/gdelt-intel` (if geopolitical only)
- `services/country-instability` (CII), `services/infrastructure-cascade` (if geopolitical)
- `services/giving`, `services/pizzint` (if only geopolitical)
- `services/market` – keep only tech-relevant symbols; remove commodities/forex/bonds if not needed
- `services/weather` – optional
- `services/wildfires`, `services/geo-convergence` (conflict/natural), `services/focal-point-detector` (if conflict-focused)
- Config: `military`, `gulf-fdi`, `irradiators`, `pipelines` (or keep only if tech-relevant), `ports` (optional)

### 3.3 Server (API) domains to KEEP

- `server/worldmonitor/news` – article summarization, dedup
- `server/worldmonitor/research` – list-hackernews-items, list-tech-events, list-trending-repos, list-arxiv-papers
- `server/worldmonitor/intelligence` – only get-country-intel-brief / classify-event if used for AI/tech; else remove or trim
- `server/worldmonitor/cyber` – list-cyber-threats
- `server/worldmonitor/infrastructure` – list-internet-outages, get-cable-health, list-service-statuses, get-temporal-baseline, record-baseline-snapshot
- `server/worldmonitor/market` – list-market-quotes, list-crypto-quotes, list-prediction-markets, get-sector-summary (tech), list-etf-flows, list-stablecoin-markets
- `server/worldmonitor/prediction` – list-prediction-markets (tech predictions)
- `server/worldmonitor/economic` – only if needed for tech (e.g. get-macro-signals); drop get-energy-prices, list-world-bank-indicators, get-energy-capacity

### 3.4 Server (API) domains to REMOVE

- `server/worldmonitor/military` – all (flights, vessels, posture, USNI, wingbits)
- `server/worldmonitor/maritime` – all
- `server/worldmonitor/unrest` – all
- `server/worldmonitor/conflict` – all (ACLED, UCDP, humanitarian)
- `server/worldmonitor/seismology` – all
- `server/worldmonitor/wildfire` – all
- `server/worldmonitor/displacement` – all
- `server/worldmonitor/climate` – all
- `server/worldmonitor/positive-events` – all
- `server/worldmonitor/giving` – all
- `server/worldmonitor/aviation` – all (or keep only if used for tech travel)
- `server/worldmonitor/economic` – trim to macro-signals only or remove

---

## 4. Map Layers – Keep vs Remove

### 4.1 Keep

- **cables** – subsea cables (tech infra)
- **outages** – internet outages
- **cyberThreats** – cyber threat layer
- **datacenters** – datacenters / AI datacenters
- **startupHubs** – startup hubs
- **cloudRegions** – cloud regions
- **techHQs** – tech HQs
- **techEvents** – tech events
- **weather** – optional

### 4.2 Remove

- conflicts, bases, pipelines, hotspots, ais, nuclear, irradiators, sanctions, waterways, economic, protests, flights, military, natural, spaceports, minerals, fires
- ucdpEvents, displacement, climate
- stockExchanges, financialCenters, centralBanks, commodityHubs, gulfInvestments
- positiveEvents, kindness, happiness, speciesRecovery, renewableInstallations, tradeRoutes

---

## 5. Configuration Files to Update

| File | Action |
|------|--------|
| `src/config/variant.ts` | Consider making tech the only variant or default; remove or hide full/finance/happy switcher for AI/tech-only build. |
| `src/config/panels.ts` | Define a single AI/tech panel set (or make tech variant the only one); remove FULL_PANELS, FINANCE_PANELS, HAPPY_PANELS; keep only TECH_PANELS (and trim TECH_PANELS to drop any non-AI/tech). |
| `src/config/feeds.ts` | Export only tech feeds (TECH_FEEDS); remove or don’t export FULL_FEEDS, FINANCE_FEEDS, HAPPY_FEEDS, INTEL_SOURCES (or replace with tech-only intel). |
| `src/config/index.ts` | Remove exports for geo/military/conflict (INTEL_HOTSPOTS, CONFLICT_ZONES, MILITARY_BASES, NUCLEAR_FACILITIES, etc.); keep TECH_COMPANIES, AI_REGULATIONS, STARTUP_HUBS, etc.; keep UNDERSEA_CABLES, MAP_URLS; remove GAMMA_IRRADIATORS, PIPELINES, PORTS, MONITORED_AIRPORTS, GULF_INVESTMENTS if unused. |
| `src/config/entities.ts` | Trim to tech/AI entities and indices/crypto only; remove defense, healthcare, energy, consumer, commodities, countries (or keep only for tech relevance). |
| `src/config/geo` (and related) | Keep only tech geo (cables, datacenters, startup hubs, cloud regions); remove conflict, bases, nuclear, waterways, sanctions, etc. |

---

## 6. Components to Remove or Stub

- **CIIPanel** – remove (or stub) and all CII data loading.
- **StrategicPosturePanel** – remove if military/vessel-based; else refactor to tech-only.
- **StrategicRiskPanel** – remove.
- **GdeltIntelPanel** – remove (or replace with tech-only intel).
- **CascadePanel** – remove (or limit to tech infra only).
- **SatelliteFiresPanel** – remove.
- **UcdpEventsPanel** – remove.
- **DisplacementPanel** – remove.
- **ClimateAnomalyPanel** – remove.
- **PopulationExposurePanel** – remove.
- **GivingPanel** – remove.
- **InvestmentsPanel** (GCC) – remove.
- **PositiveNewsFeedPanel, CountersPanel, ProgressChartsPanel, BreakthroughsTickerPanel, HeroSpotlightPanel, GoodThingsDigestPanel, SpeciesComebackPanel, RenewableEnergyPanel** – remove (happy variant).

Keep: **NewsPanel** (for tech categories), **InsightsPanel**, **MapContainer**, **MarketPanel**, **HeatmapPanel** (if tech sectors), **CommoditiesPanel** – remove; **CryptoPanel**, **PredictionPanel**, **MonitorPanel**, **EconomicPanel** – optional (keep if tech econ); **TechReadinessPanel**, **TechEventsPanel**, **ServiceStatusPanel**, **RegulationPanel**, **TechHubsPanel**, **MacroSignalsPanel**, **ETFFlowsPanel**, **StablecoinPanel**, **LiveNewsPanel**, **LiveWebcamsPanel**, **RuntimeConfigPanel**.

---

## 7. Data Loader & App Wiring

- **`src/app/data-loader.ts`**  
  - Remove: loadGovernmentSpending, loadOilAnalytics, loadPizzInt (or keep only if tech), loadNaturalEvents, loadConflict/UCDP/HAPI, loadDisplacement, loadClimate, loadPopulationExposure, loadGiving, loadFires, loadMilitaryFlights/Vessels/Posture, loadProtestEvents, loadAviationDelays, loadHappyVariant data (progress, species, renewable, happiness, kindness, positive events).  
  - Keep: loadNews (tech feeds), loadMarkets (tech symbols), loadPredictions, loadFredData (optional), loadTechEvents, loadOutages, loadCyberThreats (if used), loadCableHealth, loadInsights, loadTechReadiness, loadMonitorResults.

- **`src/app/panel-layout.ts`**  
  - Create only panels in the “Keep” list; remove creation and registration of removed panels; remove variant switcher for full/finance/happy if building AI/tech-only.

- **`src/app/event-handlers.ts`**  
  - Remove references to CII, Giving, and other removed panels; keep only tech panel toggles and live-news refresh.

- **`src/app/country-intel.ts`**  
  - Remove or refactor to tech-only (no military posture, no CII).

- **`src/app/search-manager.ts`**  
  - Remove CII/getScores and any search tied to removed panels.

---

## 8. API Routes & Middleware

- Remove or 404 routes for: military, maritime, unrest, conflict, seismology, wildfire, displacement, climate, positive-events, giving, aviation (if dropped), economic (except chosen endpoints).
- Keep: news, research, intelligence (if trimmed), cyber, infrastructure, market, prediction (tech).
- Update any gateway or middleware that routes by domain so removed domains are not called.

---

## 9. Suggested Execution Order

1. **Phase 1 – Config and panels**  
   - Add or enforce “tech-only” variant (e.g. single variant or default tech).  
   - In `panels.ts`, use only TECH_PANELS and trim to AI/tech panels; in `feeds.ts` use only TECH_FEEDS; drop INTEL_SOURCES or replace with tech-only.  
   - In `panel-layout.ts`, create only the kept panels; remove full/finance/happy-only blocks for removed panels.

2. **Phase 2 – Data loading**  
   - In `data-loader.ts`, remove all load* calls and status updates for removed panels/sources; keep only tech news, tech events, outages, cables, service status, markets (tech), crypto, predictions, insights, tech readiness.

3. **Phase 3 – Map**  
   - In `panels.ts` (or map config), set DEFAULT_MAP_LAYERS and MOBILE_DEFAULT_MAP_LAYERS to only the “Keep” layers; remove layer toggles for removed layers in UI.  
   - In map component and geo config, stop loading conflict, military, natural, fires, displacement, climate, etc.

4. **Phase 4 – Server and API**  
   - Remove or disable server handlers for military, maritime, unrest, conflict, seismology, wildfire, displacement, climate, positive-events, giving, aviation (if not needed), and trim economic.  
   - Remove corresponding generated client methods and API route registrations.

5. **Phase 5 – Cleanup**  
   - Delete or stub components listed in §6.  
   - Remove unused services and config exports (§3, §5).  
   - Remove data-freshness entries and LAYER_TO_SOURCE for removed sources.  
   - Update types (e.g. MapLayers) to drop removed layer keys if desired.  
   - Run tests and fix references (search-manager, event-handlers, country-intel).

6. **Phase 6 – Optional**  
   - Simplify variant switcher (only tech) or remove it.  
   - Adjust header/nav to match single focus (AI/tech).  
   - i18n: remove keys for removed panels/sources or leave for future.

---

## 10. Files to Touch (Checklist)

- `src/config/variant.ts`
- `src/config/panels.ts`
- `src/config/feeds.ts`
- `src/config/index.ts`
- `src/config/entities.ts`
- `src/config/geo/*` (or equivalent)
- `src/app/panel-layout.ts`
- `src/app/data-loader.ts`
- `src/app/event-handlers.ts`
- `src/app/country-intel.ts`
- `src/app/search-manager.ts`
- `src/components/index.ts` (exports)
- Map layer types and defaults (`src/types/index.ts`, map component)
- `src/services/data-freshness.ts`
- Server route registration (e.g. Convex or API router)
- `server/worldmonitor/*` (remove entire domains listed in §3.4)
- E2E and tests that reference removed panels/sources

This plan removes all sources and panels that do not pertain to AI or technology and leaves a single-focused AI/tech product surface and codebase.
