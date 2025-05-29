```
BranchlengthSampler

A type that allows you to specify a additive proposal function in the log domain and a prior distrubution over the log of the branchlengths. It also stores `acc_ratio` which is a tuple of `(ratio, total, #acceptances)`, where `ratio::Float64` is the acceptance ratio, `total::Int64` is the total number of proposals, and `#acceptances::Int64` is the number of acceptances.
```
