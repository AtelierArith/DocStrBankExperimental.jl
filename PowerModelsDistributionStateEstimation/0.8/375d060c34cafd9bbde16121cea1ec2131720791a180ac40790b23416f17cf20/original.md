```
assign_basic_individual_criteria!(data::Dict; chosen_criterion::String="rwlav")
```

Basic function that assigns individual criteria to measurements in data["meas"]. For each measurement, if the distribution type of at least one of the phases is normal, the criterion defaults to the chosen_criterion. Otherwise, it is assigned the 'mle' criterion. The function takes as input either a single measurement dictionary, e.g., data["meas"]["1"] or the full MATHEMATICAL data model.
