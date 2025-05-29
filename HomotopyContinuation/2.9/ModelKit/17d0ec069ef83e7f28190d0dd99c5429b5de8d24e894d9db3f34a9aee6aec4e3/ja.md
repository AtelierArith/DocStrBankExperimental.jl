```
to_number(x::Expression)
```

`Expression` `x`をネイティブな数値型にアンパックしようとします。

```julia-repl julia> x = to_number(Expression(2)) 2

julia> typeof(x) Int64
```
