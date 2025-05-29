```
GenericInteractionFunction{R, C, T} <: InteractionFunction{R, C, T}
```

Interaction function `R × C → T` acting as a type-safe wrapper for a given function.

# Constructor

```
GenericInteractionFunction{R, C, T}(fun)
```

Create an interaction function from the given function `fun`.

# Examples

```jldoctest; setup = :(using ImplicitArrays)
julia> f = GenericInteractionFunction{Int64, Int64, Int64}(+); f(9, 3)
12

julia> g = GenericInteractionFunction{Int64, Int64, Float64}(/); g(9, 3)
3.0

julia> h = GenericInteractionFunction{String, Int64, String}(repeat); h("abc", 3)
"abcabcabc"
```

!!! note
    The interaction function can only be evaluated if there is a method `fun(::R, ::C)` that returns a value of type `T`. Otherwise, a `MethodError` or `TypeError` is thrown.

