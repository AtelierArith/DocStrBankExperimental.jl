```
countngrams!(o, x, n, b, m=length(o))
```

`x`の`n`グラムの数を基数`b`とモジュロ`m`を使用してカウントし、結果を`o`に格納します。

# 例

```jldoctest
julia> o = zeros(Int, 5)
5-element Vector{Int64}:
 0
 0
 0
 0
 0

julia> countngrams!(o, "foo", 3, 256)
5-element Vector{Int64}:
 2
 1
 1
 0
 1
```

参照: [`countngrams`](@ref), [`ngrams`](@ref), [`ngrams!`](@ref),     [`NGramMatrix`](@ref), [`NGramIterator`](@ref).
