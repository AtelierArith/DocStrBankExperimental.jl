```julia
QDM(
    y_obs::AbstractArray{T<:Real, 1},
    y_calib::AbstractArray{T<:Real, 1},
    y_pred::AbstractArray{T<:Real, 1};
    type_adj,
    kw...
) -> Any

```

# Arguments

  * `type_adj`: 

      * `add`: 高斯分布的变量，如Tair
      * `mul`: 降水

# Notes

QDM: 需要使用一个滑动窗口。

  * `ClimDown`使用的是10年的窗口，一次处理10年；
  * `climQMBC`使用的是`nobs`的窗口，一次处理1年。

# References

1. Cannon, A. J., Sobie, S. R., & Murdock, T. Q. (2015). Bias Correction of GCM Precipitation by Quantile Mapping: How Well Do Methods Preserve Changes in Quantiles and Extremes? Journal of Climate, 28(17), 6938–6959. https://doi.org/10.1175/JCLI-D-14-00754.1
2. https://github.com/pacificclimate/ClimDown/blob/master/R/QDM.R#L126
3. https://github.com/rpkgs/climQMBC/blob/master/R/map_QDM.R#L43
