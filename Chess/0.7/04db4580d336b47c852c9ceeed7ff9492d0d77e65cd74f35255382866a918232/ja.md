```
rankfromchar(c::Char)
```

文字をランクに変換しようとします。

返り値は `Union{SquareRank, Nothing}` です。文字が有効なランクを表さない場合は `nothing` が返されます。

# 例

```julia-repl
julia> rankfromchar('2')
RANK_2

julia> rankfromchar('x') == nothing
true
```
