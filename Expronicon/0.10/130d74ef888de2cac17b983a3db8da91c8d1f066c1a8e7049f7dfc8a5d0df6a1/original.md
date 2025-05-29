```
JLFunction(ex::Expr)
```

Create a `JLFunction` object from a Julia function `Expr`.

# Example

```julia
julia> JLFunction(:(f(x) = 2))
f(x) = begin
    #= REPL[37]:1 =#    
    2    
end
```
