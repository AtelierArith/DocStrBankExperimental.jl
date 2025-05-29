```
copy!(xf::Transducer, dest, src)
```

ソース `src` をトランスデューサ `xf` に供給し、結果を `dest` に格納します。コレクション `dest` と `src` は同じ形状を持つ場合があります。ソース `src` は反復可能でなければなりません。宛先 `dest` は `empty!` と `push!` を実装している必要があります。

参照: [`map!`](@ref).

# 例

```jldoctest
julia> using Transducers

julia> copy!(opcompose(PartitionBy(x -> x ÷ 3), Map(sum)), Int[], 1:10)
4-element Vector{Int64}:
  3
 12
 21
 19
```
