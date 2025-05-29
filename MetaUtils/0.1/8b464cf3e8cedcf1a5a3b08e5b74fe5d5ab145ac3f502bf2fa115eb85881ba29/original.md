```
@show_sexpr(expr, linenums=false)
```

shows the lisp style S-expression of `expr` and prints the line number nodes if `linenums` is true.  This is the macro version of `Meta.show_sexpr`.

## Example

```julia
julia> @show_sexpr 2x+1
(:call, :+, (:call, :*, 2, :x), 1)
```

`teval` function can evaluate the output of `@show_sexpr`. 

```julia
julia> x = 10; (:call, :+, (:call, :*, 2, :x), 1) |> teval
21
```
