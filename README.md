# Airport International Arrivals — Immigration Hall Simulation Proposal

A discrete-event simulation proposal to model passenger flow through a newly
proposed international arrivals layout — from aircraft disembarkation through
passport control to baggage reclaim and exit — before construction begins.

## Objective

Build a simulation of the proposed international arrivals layout to help the
projects team:

- **Visualise** passenger flow through the new hall
- **Identify bottlenecks** — where queues, congestion, and delays are likely
  to occur under peak/off-peak conditions
- **Validate design decisions** before capital investment in construction

## What changed in the new layout

| Change | Original | Improved |
|---|---|---|
| Immigration lanes | Two (e-gates, manned desks) | Three (e-gates, manned desks, special assistance) |
| Queue guidance | None shown | Staff-directed serpentine split |
| PRM / special assistance flow | Not shown | Dedicated ambulift route bypassing main queue |
| Immigration → reclaim transition | Single narrow corridor | Dedicated buffer zone to absorb surges |
| Baggage belts | Two fixed | Two fixed + one flexible peak-activation belt |
| Passenger guidance | None | Ceiling-mounted digital signage with live wait times |

## Passenger flow paths modelled

1. **Standard passenger (airbridge):** contact stand → airbridge → serpentine
   queue → passport control → buffer zone → baggage reclaim → exit
2. **Coach passenger (remote stand):** remote stand → coach transfer (96-pax
   batch) → hall entry → serpentine queue → passport control → buffer zone →
   baggage reclaim → exit
3. **PRM / UM / special assistance:** disembarks first → ambulift or escort →
   bypasses main queue → special assistance desk → escorted to reclaim → exit

## Data required (by stakeholder team)

Seven teams feed inputs into the model — each owns a piece it can't be built
without:

| Team | Provides |
|---|---|
| Project Team | Design capacity, success criteria, layout variants |
| Border Force | Processing times, e-gate outages, visa-stamping rules |
| Operations / Dispatch | Stand allocation, ramp delays, wind thresholds, coach ops |
| Special Assistance | Agent capacity, ambulift process, PRM escort times |
| Passenger Service / Front House | Deplaning times, door malfunctions, family behaviour |
| Airside / Baggage | First/last bag times, belt allocation, trim offload delays |
| Business Analytics | Historical flight, passenger-flow, and processing-time data |

Detailed data-collection questions for each team are in the deck (slides 5–7).

## Model design

- **Agent attributes:** arrival mode, flight number, nationality/passport,
  mobility (standard/PRM), UM status, group type, bag count
- **Routing logic:** conditional rules at entry, queue split, PRM routing,
  belt allocation, and exit (trolley vs. direct)
- **Processing time distributions:** e.g. e-gates ~triangular(25s, 45s, 70s);
  manned desks vary by passport type; special assistance ~4–5 min
- **Disruption scenarios:** ramp staff shortages, high winds, aircraft trim
  delays, belt congestion, e-gate outages, door malfunctions, coach delays

## Key performance indicators tracked

- Queue wait time (serpentine + each passport control lane)
- Hall occupancy vs. fire safety capacity
- End-to-end passenger journey time
- Baggage wait time (first/last bag by flight and aircraft type)
- Bottleneck detection (which process fails first under peak demand)
- Scenario comparisons (2 vs. 3 belts, e-gate outage impact, peak vs. off-peak)

## Deliverables

- A calibrated, reusable simulation model of the new layout (built in
  AirTOP / CAST)
- A results report with visualisations (heatmaps, queue profiles, journey
  time charts)
- Evidence-based recommendations on infrastructure sizing, staffing levels,
  and layout refinements

## Estimated effort

| Phase | Hours |
|---|---|
| Data gathering & stakeholder consultation | 8–10 |
| Data cleaning, validation & preparation | 6–8 |
| Model build (AirTOP/CAST) | 15–20 |
| Calibration & validation | 5–8 |
| Scenario testing & analysis | 8–10 |
| Insight generation & presentation | 5–8 |
| **Total** | **~50–60 hrs (7–8 working days)** |

Timelines depend on data availability and stakeholder response times, and may
shift if additional scenarios or layout variants are requested.

## Repository structure

```
.
├── README.md
└── docs/
    └── Sample_Simulation_Proposal_for_Airport_Immigration_Hall.pptx
```

## Status

📋 Proposal stage — awaiting stakeholder data collection before model build
begins.
