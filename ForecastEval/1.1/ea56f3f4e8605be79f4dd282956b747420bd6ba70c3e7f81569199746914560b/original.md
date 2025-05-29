```
MCSTest(inQF::Vector{Int}, outQF::Vector{Int}, pvalueQF::Vector{Float64}, inMT::Vector{Int}, outMT::Vector{Int}, pvalueMT::Vector{Float64})
```

Output type from performing the MCS test proposed in Hansen, Lunde, Nason (2011) "The Model Confidence Set", Econometrica, 79 (2), pp. 453-497. 

The field names of this type have trailing "QF" or "MT", where QF corresponds to the quadratic form test (see section 3.1.1 of original paper), while MT corresponds to the maximum t-stat test (see section 3.1.2 of original paper). 

Note, in the fields of this type, the forecast models input to the MCS method are indicated via an integer counting up from 1 for each forecast model. These integers correspond to the columns of the input loss matrix; see ?mcs for more info. 

The fields of this type follow: 

```
inQF <- Models that are in the MCS via the quadratic form method
outQF <- Models that are not in the MCS via the quadratic form method
pvalueQF <- The cumulative p-values from the quadratic form method
inMT <- Models that are in the MCS via the max t-stat method
outMT <- Models that are not in the MCS via the max t-stat method
pvalueMT <- The cumulative p-values from the max t-stat method
```
