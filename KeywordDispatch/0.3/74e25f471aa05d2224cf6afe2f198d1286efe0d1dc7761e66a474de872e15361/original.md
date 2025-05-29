```
@kwdispatch sig [methods]
```

Designate a function signature `sig` that should dispatch on keyword arguments. A function can also be provided, in which case *all* calls to that function are will dispatch to keyword methods.

It is possible to specify keyword aliases by specifying `from => to` pairs in the keyword position.

The optional `methods` argument allows a block of keyword methods specified as anonymous functions. To define additional keyword methods, use the [`@kwmethod`](@ref) macro.

# Examples

```julia
@kwdispatch f(_)
@kwdispatch f(_::Real)

@kwdispacth f # equivalent to @kwdispatch f(_...)

@kwdispatch f(x) begin
    (a) -> x+a
    (b) -> x-b
end
# equivalent to
#  @kwdispatch f(x)
#  @kwmethod f(x;a) = x+a
#  @kwmethod f(x;b) = x-b

@kwdispatch f(; alpha=>α) # specifies alpha as an alias to α
```
