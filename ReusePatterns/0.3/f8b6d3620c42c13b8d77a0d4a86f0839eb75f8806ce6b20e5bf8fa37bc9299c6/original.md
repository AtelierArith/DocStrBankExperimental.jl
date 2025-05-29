`forward(sender::Tuple{Type,Symbol}, receiver::Type, method::Method; withtypes=true, allargs=true)`

Return a `Vector{String}` containing the Julia code to properly forward `method` calls from a `sender` type to a receiver type.

The `sender` tuple must contain a structure type, and a symbol with the name of one of its fields.

The `withtypes` keyword controls whether the forwarding method has type annotated arguments.  The `allargs` keyword controls whether all arguments should be used, or just the first ones up to the last containing the `receiver` type.

Both keywords are `true` by default, but they can be set to `false` to decrease the number of forwarded methods.

# Example:

Implement a wrapper for an `Int` object, and forward the `+` method accepting `Int`:

```julia-repl
struct Wrapper{T}
    wrappee::T
    extra
    Wrapper{T}(args...; kw...) where T = new(T(args...; kw...), nothing)
end

# Prepare and evaluate forwarding methods:
m = forward((Wrapper, :wrappee), Int, which(+, (Int, Int)))
eval.(Meta.parse.(m))

# Instantiate two wrapped `Int`
i1 = Wrapper{Int}(1)
i2 = Wrapper{Int}(2)

# And add them seamlessly
println(i1 +  2)
println( 1 + i2)
println(i1 + i2)
```
