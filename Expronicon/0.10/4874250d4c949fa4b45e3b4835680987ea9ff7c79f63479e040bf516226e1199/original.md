```
JLKwStruct(ex::Expr, typealias=nothing)
```

Create a `JLKwStruct` from given Julia struct `Expr`, with an option to attach an alias to this type name.

# Example

```julia
julia> JLKwStruct(:(struct Foo
           x::Int = 1
       end))
#= kw =# struct Foo
    #= REPL[39]:2 =#
    x::Int = 1
end
```
