```
untokenise(token::Int, W::AbstractCharSpace) -> String
```

`W`において`token`に割り当てられた部分文字列を返します。

# 例

```julia-repl
julia> untokenise(3, Alphabet)
"C"

julia> untokenise(15, Decimal^2)
"41"
```
