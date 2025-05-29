```
COSMOSAC02(components;
puremodel = PR,
userlocations = String[],
pure_userlocations = String[],
verbose = false,
reference_state = nothing)
```

## 入力パラメータ:

  * `Pi` :単一パラメータ{String}
  * `V`: 単一パラメータ{Float64}
  * `A`: 単一パラメータ{Float64}

## 説明

COSMO-RS法に基づく分子溶媒和を用いた活動係数モデル。

## 参考文献

1. Klamt, A. (1995). Conductor-like screening model for real solvents: A new approach to the quantitative calculation of solvation phenomena. Journal of Physical Chemistry, 99(7), 2224–2235. [doi:10.1021/j100007a062](https://doi.org/10.1021/j100007a062)
2. Lin, S-T. & Sandler, S.I. (2002). A priori phase equilibrium prediction from a segment contribution solvation model. Industrial & Engineering Chemistry Research, 41(5), 899–913. [doi:10.1021/ie001047w](https://doi.org/10.1021/ie001047w)
