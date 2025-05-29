```
WalkerIdeal <: WalkerIdealModel

WalkerIdeal(components; 
userlocations = String[],
group_userlocations = String[]
verbose = false)
```

## Input parameters

  * `Mw`: Single Parameter (`Float64`) - Molecular Weight `[g/mol]`
  * `Nrot`: Single Parameter (`Int`)
  * `theta1`: Single Parameter (`Float64`)
  * `theta2`: Single Parameter (`Float64`)
  * `theta3`: Single Parameter (`Float64`)
  * `theta4`: Single Parameter (`Float64`)
  * `deg1`: Single Parameter (`Int`)
  * `deg2`: Single Parameter (`Int`)
  * `deg3`: Single Parameter (`Int`)
  * `deg4`: Single Parameter (`Int`)

## Description

Walker [1] Group Contribution Ideal Model.

```
Cpᵢ(T)/R = (5+NRot)/2 ∑νᵢₖ∑gₖᵥ(θₖᵥ/T)^2*exp(θₖᵥ/T)/(1-exp(θₖᵥ/T)) , v ∈ 1:4 
```

## References

1. Walker, P. J., & Haslam, A. J. (2020). A new predictive group-contribution ideal-heat-capacity model and its influence on second-derivative properties calculated using a free-energy equation of state. Journal of Chemical and Engineering Data, 65(12), 5809–5829. [doi:10.1021/acs.jced.0c00723](https://doi.org/10.1021/acs.jced.0c00723)
