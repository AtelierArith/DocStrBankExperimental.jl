```
struct ConstInteractionFunction{R, C, T} <: InteractionFunction{R, C, T}
```

Interaction function `R × C → T` that ignores its arguments and returns a fixed value.

# Constructor

```
ConstInteractionFunction{R, C, T}(val)
```

Create a constant interaction function that always returns `val`.

# Examples

```jldoctest; setup = :(using ImplicitArrays)
julia> f = ConstInteractionFunction{Float64, Float64, Int64}(42);

julia> f(1.0, 1.5)
42
```
