```
($)(f::Function, args...)
```

Partially apply the given arguments to f. Typically used as infix `f $ args`

The returned function is of type [`PartialFunctions.PartialFunction{nothing, nothing, typeof(f), typeof(args)}`](@ref)

# Examples

```jldoctest
julia> using PartialFunctions

julia> simonsays = println $ "Simon says: "
println("Simon says: ", ...)

julia> simonsays("Partial function application is cool!")
Simon says: Partial function application is cool!
```
