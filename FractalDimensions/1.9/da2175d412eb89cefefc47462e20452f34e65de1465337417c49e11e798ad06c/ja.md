```
grassberger_proccacia_dim(X::AbstractStateSpaceSet, εs = estimate_boxsizes(data); kwargs...)
```

GrassbergerとProccaciaの手法[Grassberger1983](@cite)を使用し、[Theiler1986](@cite)による修正を加えて、`X`の相関次元`Δ_C`を推定します。

この関数は非常に単純なことを行います：

```julia
cm = correlationsum(data, εs; kwargs...)
Δ_C = slopefit(rs, ys)(log2.(sizes), log2.(cm))[1]
```

つまり、さまざまな半径に対して[`correlationsum`](@ref)を計算し、相関和の対数とlog(ε)のプロットにおける線形領域を見つけようとします。

利用可能なキーワードについては[`correlationsum`](@ref)を参照してください。また、[`takens_best_estimate_dim`](@ref)、[`boxassisted_correlation_dim`](@ref)もご覧ください。
