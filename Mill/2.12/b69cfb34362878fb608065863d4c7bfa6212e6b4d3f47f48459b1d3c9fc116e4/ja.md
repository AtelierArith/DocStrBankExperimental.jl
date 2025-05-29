```
countngrams(o, x, n, b, m)
```

`x`の`n`グラムの数を、基数`b`とモジュロ`m`を使用して、`x`が単一のシーケンスの場合は長さ`m`のベクターに、`x`がシーケンスのイテラブルの場合は`m`行の行列にカウントします。

# 例

```jldoctest
julia> countngrams("foo", 3, 256, 5)
5-element Vector{Int64}:
 2
 1
 1
 0
 1

julia> countngrams(["foo", "bar"], 3, 256, 5)
5×2 Matrix{Int64}:
 2  1
 1  0
 1  2
 0  0
 1  2
```

参照: [`countngrams!`](@ref), [`ngrams`](@ref), [`ngrams!`](@ref),     [`NGramMatrix`](@ref), [`NGramIterator`](@ref).
