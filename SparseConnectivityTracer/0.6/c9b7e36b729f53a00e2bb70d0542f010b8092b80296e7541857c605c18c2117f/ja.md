```
TracerLocalSparsityDetector <: ADTypes.AbstractSparsityDetector
```

[ADTypes.jl](https://github.com/SciML/ADTypes.jl)のスパース性検出フレームワークとの統合のためのシングルトン構造体です。

入力点 `x` における局所的なスパース性パターンを計算します。グローバルなスパース性パターンについては、[`TracerSparsityDetector`](@ref)を使用してください。

# 例

局所的なスパース性パターンはグローバルパターンよりも保守的ではなく、各入力 `x` に対して再計算する必要があります：

```jldoctest
julia> using SparseConnectivityTracer

julia> detector = TracerLocalSparsityDetector()
TracerLocalSparsityDetector()

julia> f(x) = x[1] * x[2]; # J_f = [x[2], x[1]]

julia> jacobian_sparsity(f, [1, 0], detector)
1×2 SparseArrays.SparseMatrixCSC{Bool, Int64} with 1 stored entry:
 ⋅  1

julia> jacobian_sparsity(f, [0, 1], detector)
1×2 SparseArrays.SparseMatrixCSC{Bool, Int64} with 1 stored entry:
 1  ⋅

julia> jacobian_sparsity(f, [0, 0], detector)
1×2 SparseArrays.SparseMatrixCSC{Bool, Int64} with 0 stored entries:
 ⋅  ⋅

julia> jacobian_sparsity(f, [1, 1], detector)
1×2 SparseArrays.SparseMatrixCSC{Bool, Int64} with 2 stored entries:
 1  1
```

`TracerLocalSparsityDetector`は、比較や`ifelse`文を含む関数のスパース性パターンを計算できます：

```jldoctest
julia> f(x) = x[1] > x[2] ? x[1:3] : x[2:4];

julia> jacobian_sparsity(f, [1, 2, 3, 4], TracerLocalSparsityDetector())
3×4 SparseArrays.SparseMatrixCSC{Bool, Int64} with 3 stored entries:
 ⋅  1  ⋅  ⋅
 ⋅  ⋅  1  ⋅
 ⋅  ⋅  ⋅  1

julia> jacobian_sparsity(f, [2, 1, 3, 4], TracerLocalSparsityDetector())
3×4 SparseArrays.SparseMatrixCSC{Bool, Int64} with 3 stored entries:
 1  ⋅  ⋅  ⋅
 ⋅  1  ⋅  ⋅
 ⋅  ⋅  1  ⋅
```

```jldoctest
julia> f(x) = x[1] + max(x[2], x[3]) * x[3] + 1/x[4];

julia> hessian_sparsity(f, [1.0, 2.0, 3.0, 4.0], TracerLocalSparsityDetector())
4×4 SparseArrays.SparseMatrixCSC{Bool, Int64} with 2 stored entries:
 ⋅  ⋅  ⋅  ⋅
 ⋅  ⋅  ⋅  ⋅
 ⋅  ⋅  1  ⋅
 ⋅  ⋅  ⋅  1
```
