```
TracerSparsityDetector <: ADTypes.AbstractSparsityDetector
```

[ADTypes.jl](https://github.com/SciML/ADTypes.jl)のスパース性検出フレームワークとの統合のためのシングルトン構造体です。

入力ドメイン全体にわたるグローバルなスパース性パターンを計算します。特定の入力点でのローカルなスパース性パターンについては、[`TracerLocalSparsityDetector`](@ref)を使用してください。

# 例

```jldoctest
julia> using SparseConnectivityTracer

julia> detector = TracerSparsityDetector()
TracerSparsityDetector()

julia> jacobian_sparsity(diff, rand(4), detector)
3×4 SparseArrays.SparseMatrixCSC{Bool, Int64} with 6 stored entries:
 1  1  ⋅  ⋅
 ⋅  1  1  ⋅
 ⋅  ⋅  1  1

julia> f(x) = x[1] + x[2]*x[3] + 1/x[4];

julia> hessian_sparsity(f, rand(4), detector)
4×4 SparseArrays.SparseMatrixCSC{Bool, Int64} with 3 stored entries:
 ⋅  ⋅  ⋅  ⋅
 ⋅  ⋅  1  ⋅
 ⋅  1  ⋅  ⋅
 ⋅  ⋅  ⋅  1
```
