```
@hygienize(ex::Expr)
```

A macro to transform a quote by replacing variable definitions with gensymed symbols.

```julia
julia> using Hygienic

julia> @hygienize quote
           x = 1
           x + y
       end
quote
    #= REPL[2]:2 =#
    var"##x#274" = 1
    #= REPL[2]:3 =#
    var"##x#274" + y
end
```
