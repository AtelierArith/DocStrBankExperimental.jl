```
calculate_coeffs(result::Union{BFGSResult, CompositeBFGSResult}
                 logAge::AbstractVector{<:Number},
                 metallicities::AbstractVector{<:Number})
```

最適化された金属量モデル、金属量分散モデル、およびBFGS最適化の結果からの恒星質量係数を使用して、SSPごとの恒星質量係数（$r_{j,k}$は[導出](@ref mzr_derivation)における）を返します。提供された`result`が最大事後確率推定と最大尤度推定（MLE）の両方を含む`CompositeBFGSResult`である場合、係数を構築するためにMLEが使用されます。
