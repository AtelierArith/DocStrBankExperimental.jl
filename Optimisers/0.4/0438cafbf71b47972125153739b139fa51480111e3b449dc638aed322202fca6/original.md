```
Optimisers.apply!(rule::RuleType, state, parameters, gradient) -> (state, gradient)
```

This defines the action of any optimisation rule. It should return the modified gradient which will be subtracted from the parameters, and the updated state (if any) for use at the next iteration, as a tuple `(state, gradient)`.

For efficiency it is free to mutate the old state, but only what is returned will be used. Ideally this should check `maywrite(x)`, which the built-in rules do via [`@..`](@ref).

The initial state is `init(rule::RuleType, parameters)`.

# Example

```jldoctest
julia> Optimisers.init(Descent(0.1), Float32[1,2,3]) === nothing
true

julia> Optimisers.apply!(Descent(0.1), nothing, Float32[1,2,3], [4,5,6])
(nothing, Base.Broadcast.Broadcasted{Base.Broadcast.DefaultArrayStyle{1}}(*, ([4, 5, 6], 0.1f0)))
```
