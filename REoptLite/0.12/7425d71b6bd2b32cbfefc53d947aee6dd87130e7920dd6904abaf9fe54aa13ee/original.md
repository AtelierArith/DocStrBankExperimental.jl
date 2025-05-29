```
simulate_outages(;batt_kwh=0, batt_kw=0, pv_kw_ac_hourly=[], init_soc=[], critical_loads_kw=[], 
    wind_kw_ac_hourly=[], batt_roundtrip_efficiency=0.829, diesel_kw=0, fuel_available=0, b=0, m=0, 
    diesel_min_turndown=0.3
)
```

Time series simulation of outages starting at every time step of the year. Used to calculate how many time steps the  critical load can be met in every outage, which in turn is used to determine probabilities of meeting the critical load.

# Arguments

  * `batt_kwh`: float, battery storage capacity
  * `batt_kw`: float, battery inverter capacity
  * `pv_kw_ac_hourly`: list of floats, AC production of PV system
  * `init_soc`: list of floats between 0 and 1 inclusive, initial state-of-charge
  * `critical_loads_kw`: list of floats
  * `wind_kw_ac_hourly`: list of floats, AC production of wind turbine
  * `batt_roundtrip_efficiency`: roundtrip battery efficiency
  * `diesel_kw`: float, diesel generator capacity
  * `fuel_available`: float, gallons of diesel fuel available
  * `b`: float, diesel fuel burn rate intercept coefficient (y = m*x + b*rated_capacity)  [gal/kwh/kw]
  * `m`: float, diesel fuel burn rate slope (y = m*x + b*rated_capacity)  [gal/kWh]
  * `diesel_min_turndown`: minimum generator turndown in fraction of generator capacity (0 to 1)

Returns a dict

```
    "resilience_by_timestep": vector of time steps that critical load is met for outage starting in every time step,
    "resilience_hours_min": minimum of "resilience_by_timestep",
    "resilience_hours_max": maximum of "resilience_by_timestep",
    "resilience_hours_avg": average of "resilience_by_timestep",
    "outage_durations": vector of integers for outage durations with non zero probability of survival,
    "probs_of_surviving": vector of probabilities corresponding to the "outage_durations",
    "probs_of_surviving_by_month": vector of probabilities calculated on a monthly basis,
    "probs_of_surviving_by_hour_of_the_day":vector of probabilities calculated on a hour-of-the-day basis,
}
```
