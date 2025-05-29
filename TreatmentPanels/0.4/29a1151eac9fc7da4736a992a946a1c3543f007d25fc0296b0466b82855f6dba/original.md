```
BalancedPanel{TreatmentType}
```

A TreatmentPanel in which all N treatment units are observed for the same T periods.

The object is constructed from a `DataFrame` which contains all outcome and covariate data. The  constructor requires passing information on which column in the `DataFrame` holds the subject and  time period identifiers, as well as information on the timing of treatment. Treatments are specified as a `Pair` of either a `String` or `Symbol` identifying the unit treated, and a `Date` or `Int` value, identifying the treatment period. Where treatments have an end point, the treatment period os specified as a `Tuple` of either `Date` or `Int`, indicating the first and last period of treatment. Where individual units have multiple treatment periods, these are specified as a `Pair{Union{String, Symbol}, Vector{Union{Int, Date}}}` of treatment unit identifier and vector of timings. Finally, single continuous, single periodic, and multiple period treatments can be generalized to multiple treated units. The following table provides an overview of the types of treatment pattern supported:

|                    |        Only starting point |                     Start and end point |                      Multiple start & end points |
| ------------------:| --------------------------:| ---------------------------------------:| ------------------------------------------------:|
|       **one unit** |         Pair{String, Date} |         Pair{String, Tuple{Date, Date}} |         Pair{String}, Vector{Tuple{Date, Date}}} |
| **multiple units** | Vector{Pair{String, Date}} | Vector{Pair{String, Tuple{Date, Date}}} | Vector{Pair{String}, Vector{Tuple{Date, Date}}}} |
