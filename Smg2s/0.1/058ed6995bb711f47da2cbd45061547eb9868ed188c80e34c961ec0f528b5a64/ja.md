```
Nilp(vec::AbstractVector, diag::Ti, size::Ti) where{Ti <: Integer}
```

ユーザー提供のベクトルから次元が `size` の nilpotent 行列を作成します。nilpotent 行列の非ゼロ対角線は、オフセット `diag` のものとして設定されます。したがって、与えられた `vector` のサイズは少なくとも `size-diag` である必要があります。

## 例

```jldoctest; setup = :(using SMG2S; using SparseArrays)
julia> vec=[1; 1; 0; 1; 1; 1; 0]
7-element Vector{Int64}:
 1
 1
 0
 1
 1
 1
 0

julia> SMG2S.Nilp(vec, 3, 8)
┌ Info: 与えられた nilpotent 行列の次数は:
└   degree = 3
Nilpotent{Int64}(1, 8, 3,
 ⋅  ⋅  ⋅  1  ⋅  ⋅  ⋅  ⋅
 ⋅  ⋅  ⋅  ⋅  1  ⋅  ⋅  ⋅
 ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅
 ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  1  ⋅
 ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  1
 ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅
 ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅
 ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅)

```
