```
@show_texpr(expr, linenums=false)
```

Yet another `@show_sexpr`.  It shows the lisp style S-expression of `expr` and prints the line number nodes if `linenums` is true.

Remark: The indentation is different from `@show_sexpr`.

## Example

```julia
julia> @show_texpr 2x+1
(:call, :+, 
    (:call, :*, 2, :x), 1)
```

`teval` function can evaluate the output of `@show_texpr`.

```julia
julia> x = 10; (:call, :+, 
    (:call, :*, 2, :x), 1) |> teval
21
```
