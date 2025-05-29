```
conditioned(model::Model)
```

Return the conditioned values in `model`.

# Examples

```jldoctest
julia> using Distributions

julia> using DynamicPPL: conditioned, contextualize

julia> @model function demo()
           m ~ Normal()
           x ~ Normal(m, 1)
       end
demo (generic function with 2 methods)

julia> m = demo();

julia> # Returns all the variables we have conditioned on + their values.
       conditioned(condition(m, x=100.0, m=1.0))
(x = 100.0, m = 1.0)

julia> # Nested ones also work (note that `PrefixContext` does nothing to the result).
       cm = condition(contextualize(m, PrefixContext{:a}(condition(m=1.0))), x=100.0);

julia> conditioned(cm)
(x = 100.0, m = 1.0)

julia> # Since we conditioned on `m`, not `a.m` as it will appear after prefixed,
       # `a.m` is treated as a random variable.
       keys(VarInfo(cm))
1-element Vector{VarName{Symbol("a.m"), typeof(identity)}}:
 a.m

julia> # If we instead condition on `a.m`, `m` in the model will be considered an observation.
       cm = condition(contextualize(m, PrefixContext{:a}(condition(var"a.m"=1.0))), x=100.0);

julia> conditioned(cm).x
100.0

julia> conditioned(cm).var"a.m"
1.0

julia> keys(VarInfo(cm)) # <= no variables are sampled
VarName[]
```
