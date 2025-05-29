```
dimensionality(g::PeriodicGraph{N}) where N
```

`g`の各連結成分の実際の次元を決定します。各エントリ `n => [(l1,m1), (l2,m2), ...]` を持つ辞書を返します。ここで `li` は次元 `n` の連結成分を形成する頂点のリストであり、その成分は単位セルあたり `mi` 回存在します。

言い換えれば、連結成分 `li` は、現在のものよりも `mi` 倍大きな単位セルでのみ表現できる周期性を持っています。詳細は [`split_catenation`](@ref) を参照してください。

## 例

```jldoctest
julia> dimensionality(PeriodicGraph("2   1 1  1 0   2 2  -1 1   3 3  1 0   3 3  0 1"))
Dict{Int64, Vector{Tuple{Vector{Int64}, Int64}}} with 2 entries:
  2 => [([3], 1)]
  1 => [([1], 1), ([2], 1)]

julia> dimensionality(PeriodicGraph("1   1 1  2"))
Dict{Int64, Vector{Tuple{Vector{Int64}, Int64}}} with 1 entry:
  1 => [([1], 2)]
```
