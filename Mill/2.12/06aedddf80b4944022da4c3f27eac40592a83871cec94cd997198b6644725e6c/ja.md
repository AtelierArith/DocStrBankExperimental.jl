```
ngrams(o, x, n=3, b=256)
```

基数 `b` を使用して `x` の `n` グラムのコードを返します。

# 例

```jldoctest
julia> ngrams("foo", 3, 256)
5-element Vector{Int64}:
  131686
  157295
 6713199
 7302915
 7275267
```

参照: [`ngrams!`](@ref), [`countngrams`](@ref),     [`countngrams!`](@ref), [`NGramMatrix`](@ref), [`NGramIterator`](@ref).
