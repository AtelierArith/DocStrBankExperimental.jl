```
Nilp(vector::AbstractVector, size::Ti) where {Ti<:Integer}
```

ユーザー提供のベクトルから次元が `size` のニルポテント行列を作成します。ニルポテント行列の非ゼロ対角線はオフセット `1` のものとして固定されています。したがって、与えられた `vector` のサイズは少なくとも `size-1` である必要があります。

## 例

```jldoctest; setup = :(using SMG2S)
julia> vec=[1; 1; 0; 1; 1; 1; 0]
7-element Vector{Int64}:
 1
 1
 0
 1
 1
 1
 0

julia> SMG2S.Nilp(vec, 8)
Nilpotent{Int64}(3, 8, 4,
  ⋅   1.0   ⋅    ⋅    ⋅    ⋅    ⋅    ⋅
  ⋅    ⋅   1.0   ⋅    ⋅    ⋅    ⋅    ⋅
  ⋅    ⋅    ⋅    ⋅    ⋅    ⋅    ⋅    ⋅
  ⋅    ⋅    ⋅    ⋅   1.0   ⋅    ⋅    ⋅
  ⋅    ⋅    ⋅    ⋅    ⋅   1.0   ⋅    ⋅
  ⋅    ⋅    ⋅    ⋅    ⋅    ⋅   1.0   ⋅
  ⋅    ⋅    ⋅    ⋅    ⋅    ⋅    ⋅    ⋅
  ⋅    ⋅    ⋅    ⋅    ⋅    ⋅    ⋅    ⋅ )
```
