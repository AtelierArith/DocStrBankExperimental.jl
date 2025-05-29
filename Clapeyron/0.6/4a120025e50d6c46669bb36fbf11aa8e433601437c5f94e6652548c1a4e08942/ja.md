```
COSMOSAC10(components;
puremodel = PR,
userlocations = String[],
pure_userlocations = String[],
verbose = false,
reference_state = nothing)
```

## 入力パラメータ:

  * `Pnhb` :単一パラメータ{String}
  * `POH` :単一パラメータ{String}
  * `POT` :単一パラメータ{String}
  * `V`: 単一パラメータ{Float64}
  * `A`: 単一パラメータ{Float64}

## 説明

COSMO-RS法に基づく分子溶媒和を使用した活動係数モデル。シグマプロファイルは、非水素結合、水素受容体および水素供与体によって分割されています。

## 参考文献

1. Klamt, A. (1995). Conductor-like screening model for real solvents: A new approach to the quantitative calculation of solvation phenomena. Journal of Physical Chemistry, 99(7), 2224–2235. [doi:10.1021/j100007a062](https://doi.org/10.1021/j100007a062)
2. Lin, S-T. & Sandler, S.I. (2002). A priori phase equilibrium prediction from a segment contribution solvation model. Industrial & Engineering Chemistry Research, 41(5), 899–913. [doi:10.1021/ie001047w](https://doi.org/10.1021/ie001047w)
3. Hsieh, C-H., Sandler, S.I., & Lin, S-T. (2010). Improvements of COSMO-SAC for vapor–liquid and liquid–liquid equilibrium predictions. Fluid Phase Equilibria, 297(1), 90-97. [doi:10.1016/j.fluid.2010.06.011](https://doi.org/10.1016/j.fluid.2010.06.011)
