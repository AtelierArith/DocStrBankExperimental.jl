```
tokenise(s::String, W::AbstractCharSpace) -> Int, Nothing
```

`s`に割り当てられたトークンを返します。

`s`が`W`にない場合は`nothing`を返します。

# 例

```julia-repl
julia> tokenise("C", Alphabet)
3

julia> tokenise("1", Alphabet)

julia> tokenise("01", Decimal^2)
11

```
