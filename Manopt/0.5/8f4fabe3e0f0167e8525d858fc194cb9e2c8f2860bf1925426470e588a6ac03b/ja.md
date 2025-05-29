```
X = get_subtrahend_gradient(amp, q)
get_subtrahend_gradient!(amp, X, q)
```

サブトラヘンド `h` の (サブ)勾配を [`ManifoldDifferenceOfConvexObjective`](@ref) `amp` の点 `q` で評価します ( `X` の代わりに)。

評価は `!` バリアントのために `X` の代わりに行われます。`T=`[`AllocatingEvaluation`](@ref) 問題は、内部でメモリを割り当てる可能性があります。非変異バリアントが `T=`[`InplaceEvaluation`](@ref) で呼び出されると、結果のためにメモリが割り当てられます。
