```julia
QDM(
    y_obs::AbstractArray{T<:Real, 1},
    y_calib::AbstractArray{T<:Real, 1},
    y_pred::AbstractArray{T<:Real, 1};
    type_adj,
    kw...
) -> Any

```

# 引数

  * `type_adj`: 

      * `add`: 高斯分布の変数、例えばTair
      * `mul`: 降水

# 注意事項

QDM: スライディングウィンドウを使用する必要があります。

  * `ClimDown`は10年のウィンドウを使用し、一度に10年を処理します；
  * `climQMBC`は`nobs`のウィンドウを使用し、一度に1年を処理します。

# 参考文献

1. Cannon, A. J., Sobie, S. R., & Murdock, T. Q. (2015). Bias Correction of GCM Precipitation by Quantile Mapping: How Well Do Methods Preserve Changes in Quantiles and Extremes? Journal of Climate, 28(17), 6938–6959. https://doi.org/10.1175/JCLI-D-14-00754.1
2. https://github.com/pacificclimate/ClimDown/blob/master/R/QDM.R#L126
3. https://github.com/rpkgs/climQMBC/blob/master/R/map_QDM.R#L43
