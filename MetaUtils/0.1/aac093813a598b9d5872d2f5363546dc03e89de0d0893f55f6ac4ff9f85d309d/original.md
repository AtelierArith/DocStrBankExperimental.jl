```
@show_expr(expr, linenums=false)
```

shows the Juia style expression of `expr` and prints the line number nodes if `linenums` is true.  This is the macro version of `show_expr`.

## Example

```julia
julia> @show_expr 2x+1
Expr(:call, :+, 
    Expr(:call, :*, 2, :x), 1)
```

`eval` function can evaluate the output of `@show_expr`. 

```julia
julia> x = 10; Expr(:call, :+, 
    Expr(:call, :*, 2, :x), 1) |> eval
21
```
