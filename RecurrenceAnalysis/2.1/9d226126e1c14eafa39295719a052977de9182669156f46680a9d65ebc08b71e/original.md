```
vl_entropy(R[; lmin=2, theiler])
```

Calculate the Shannon entropy of the vertical lines contained in the recurrence matrix `R`, ruling out the lines shorter than `lmin` (2 by default) and all the points inside the Theiler window (see [`rqa`](@ref) for the default values and usage of the keyword argument `theiler`).

Notes: This metric was first proposed in the paper "Exploiting Nonlinear Recurrence and Fractal Scaling Properties for Voice Disorder Detection" as Recurrence Period Density Entropy or Recurrence Probability Density Entropy (RPDE). It is a normalized dimensionless metric in the range [0,1]. In the 2018 article "Recurrence threshold selection for obtaining robust recurrence characteristics in different embedding dimensions", the indicator RPDE is explicitly called Recurrence Time Entropy (RTE). Here RPDE and RTE are clearly the same indicator.
