```
mdd(Sn::AbstractVector{T}) where T<:AbstractFloat
```

投資の最大ドローダウン（MDD）を計算します。また、[`sn`](@ref)、[`mer`](@ref)、[`ann_std`](@ref)、[`apy`](@ref)、[`ann_sharpe`](@ref)、[`calmar`](@ref)、および[`opsmetrics`](@ref)も参照してください。

# 引数

  * `Sn::AbstractVector{T}`: 投資期間中の累積資産。詳細は[`sn`](@ref)を参照してください。

# 戻り値

  * `::AbstractFloat`: 投資のMDD。
