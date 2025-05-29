```
fixedmass_correlation_dim(X [, max_j]; kwargs...)
```

固定質量アルゴリズムを使用して相関和を計算し、その結果を使用して `X` の相関次元 `Δ_M` を計算します。

この関数は非常に単純なことを行います：

```julia
rs, ys = fixedmass_correlationsum(X, args...; kwargs...)
slopefit(rs, ys)[1]
```
