```
ancestralreconstruction(fr::AbstractDataFrame, net::HybridNetwork; kwargs...)
```

ネットワーク上の祖先の特性を推定します。これは、先端にあるデータを考慮に入れます。データに対して切片を用いた系統回帰を行うために、関数 [`phylolm`](@ref) を使用します（これはネットワーク上で進化モデルを適合させることに相当します）。

詳細については、[`phylolm`](@ref) および `ancestralreconstruction(obj::PhyloNetworkLinearModel[, X_n::Matrix])` のドキュメントを参照してください。

[`ReconstructedStates`](@ref) 型のオブジェクトを返します。
