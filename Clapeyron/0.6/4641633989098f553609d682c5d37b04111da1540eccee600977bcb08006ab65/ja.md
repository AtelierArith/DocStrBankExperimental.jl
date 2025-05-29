```
WalkerIdeal <: WalkerIdealModel

WalkerIdeal(components; 
userlocations = String[],
group_userlocations = String[]
verbose = false)
```

## 入力パラメータ

  * `Mw`: 単一パラメータ (`Float64`) - 分子量 `[g/mol]`
  * `Nrot`: 単一パラメータ (`Int`)
  * `theta1`: 単一パラメータ (`Float64`)
  * `theta2`: 単一パラメータ (`Float64`)
  * `theta3`: 単一パラメータ (`Float64`)
  * `theta4`: 単一パラメータ (`Float64`)
  * `deg1`: 単一パラメータ (`Int`)
  * `deg2`: 単一パラメータ (`Int`)
  * `deg3`: 単一パラメータ (`Int`)
  * `deg4`: 単一パラメータ (`Int`)

## 説明

Walker [1] グループ寄与理想モデル。

```
Cpᵢ(T)/R = (5+NRot)/2 ∑νᵢₖ∑gₖᵥ(θₖᵥ/T)^2*exp(θₖᵥ/T)/(1-exp(θₖᵥ/T)) , v ∈ 1:4 
```

## 参考文献

1. Walker, P. J., & Haslam, A. J. (2020). A new predictive group-contribution ideal-heat-capacity model and its influence on second-derivative properties calculated using a free-energy equation of state. Journal of Chemical and Engineering Data, 65(12), 5809–5829. [doi:10.1021/acs.jced.0c00723](https://doi.org/10.1021/acs.jced.0c00723)
