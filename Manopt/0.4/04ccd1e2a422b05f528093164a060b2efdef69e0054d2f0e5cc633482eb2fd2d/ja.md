```
get_gradient(M::AbstractManifold, mgo::AbstractManifoldGradientObjective{T}, p)
get_gradient!(M::AbstractManifold, X, mgo::AbstractManifoldGradientObjective{T}, p)
```

[`AbstractManifoldGradientObjective{T}`](@ref) `mgo` の `p` における勾配を評価します。

評価は `!` バリアントのために `X` の場所で行われます。`T=`[`AllocatingEvaluation`](@ref) 問題は内部でメモリを割り当てる可能性があります。非変異バリアントが `T=`[`InplaceEvaluation`](@ref) で呼び出されると、結果のためのメモリが割り当てられます。

パラメータの順序は `Manifolds.jl` の哲学に従っており、変異バリアントであっても、マニフォールドが最初のパラメータであり、（インプレースの）接ベクトル `X` が2番目に来ることに注意してください。
