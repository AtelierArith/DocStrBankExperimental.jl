```
X = get_subtrahend_gradient(amp, q)
get_subtrahend_gradient!(amp, X, q)
```

サブトラヘンド `h` の (サブ)勾配を [`ManifoldDifferenceOfConvexObjective`](@ref) `amp` の点 `q` で評価します (結果は `X` に格納されます)。

評価は `!` バリアントのために `X` に格納されます。`T=`[`AllocatingEvaluation`](@ref) 問題はまだメモリを割り当てる可能性があります。非変異バリアントが `T=`[`InplaceEvaluation`](@ref) で呼び出されると、結果のためにメモリが割り当てられます。
