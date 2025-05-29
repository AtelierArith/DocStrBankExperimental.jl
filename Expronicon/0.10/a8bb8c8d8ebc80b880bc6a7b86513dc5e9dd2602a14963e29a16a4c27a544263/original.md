```
JLStruct(ex::Expr)
```

Create a `JLStruct` object from a Julia struct `Expr`.

# Example

```julia
julia> JLStruct(:(struct Foo
           x::Int
       end))
struct Foo
    #= REPL[38]:2 =#
    x::Int
end
```
