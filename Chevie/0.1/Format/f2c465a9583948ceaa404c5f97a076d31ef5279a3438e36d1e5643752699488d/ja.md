`joindigits(l::AbstractVector{Int},delim="()";sep=",")`

リスト `l` の (通常は小さい) 数字をできるだけコンパクトに表示します: すべての数字が10未満の場合は区切り文字はありません。

```julia-repl
julia> joindigits([1,9,3,5])
"1935"

julia> joindigits([1,10,3,5])
"(1,10,3,5)"

julia> joindigits([1,10,3,5],"[]";sep="-")
"[1-10-3-5]"
```
