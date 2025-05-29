```
assign_load_pseudo_measurement_info!(data::Dict, pseudo_load_list::Array, cluster_list::Array; time_step::Int64=1, day::Int64=1)
```

This function is a helper function to associate pseudo measurement information to a list of loads.     #Arguments:     - data: `ENGINEERING` data model of the feeder, or dictionary corresponding to a single measurement     - pseudo*load*list: list of loads that are described by pseudo measurements     - cluster*list: list of clusters to be associated one-on-one with the pseudo*load*list     - time*step: time step to extract the probability distribuion function for, if applicable     - day: day to extract the probability distribuion function for, if applicable
