```
simulate_outages(d::Dict, p::REoptInputs; microgrid_only::Bool=false)
```

Time series simulation of outages starting at every time step of the year. Used to calculate how many time steps the  critical load can be met in every outage, which in turn is used to determine probabilities of meeting the critical load.

# Arguments

  * `d`::Dict from `reopt_results`
  * `p`::REoptInputs the inputs that generated the Dict from `reopt_results`
  * `microgrid_only`::Bool whether or not to simulate only the optimal microgrid capacities or the total capacities. This input is only relevant when modeling multiple outages.

Returns a dict

```julia
{
    "resilience_by_time_step": vector of time steps that critical load is met for outage starting in every time step,
    "resilience_hours_min": minimum of "resilience_by_time_step",
    "resilience_hours_max": maximum of "resilience_by_time_step",
    "resilience_hours_avg": average of "resilience_by_time_step",
    "outage_durations": vector of integers for outage durations with non zero probability of survival,
    "probs_of_surviving": vector of probabilities corresponding to the "outage_durations",
    "probs_of_surviving_by_month": vector of probabilities calculated on a monthly basis,
    "probs_of_surviving_by_hour_of_the_day":vector of probabilities calculated on a hour-of-the-day basis,
}
```
