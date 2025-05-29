```
create_partial_cxx_identity(n::I_1, idxs::Vector{I_2}) where {I_1 <: Integer, I_2 <: Integer}
```

形状が (`n`, `length(idxs)`) の CxxPtr{CxxPtr{Float64}} 型（C++ の double** のラッパー）の行列を作成します。列は `idxs` のエントリに対応する標準基底ベクトルです。基底ベクトルの順序は `idxs` のインデックスの順序によって定義されます。アプリケーションに関する詳細はこの [guide](@ref "Seed-Matrix") で見つけることができます。

!!! warning
    行数 `n` は `idxs` の最大インデックスより小さくなければなりません！


!!! warning
    `idxs` の値は非負でなければなりません！


# 例

```jldoctest
n = 4
idxs = [1, 3]
id = CxxMatrix(create_partial_cxx_identity(n, idxs), n, length(idxs))
# 出力

4×2 CxxMatrix:
 1.0  0.0
 0.0  0.0
 0.0  1.0
 0.0  0.0
```

`idxs` の順序は基底ベクトルの順序を定義します。

```jldoctest
n = 3
idxs = [3, 0, 1]
id = CxxMatrix(create_partial_cxx_identity(n, idxs), n, length(idxs))


# 出力

3×3 CxxMatrix:
 0.0  0.0  1.0
 0.0  0.0  0.0
 1.0  0.0  0.0
```
