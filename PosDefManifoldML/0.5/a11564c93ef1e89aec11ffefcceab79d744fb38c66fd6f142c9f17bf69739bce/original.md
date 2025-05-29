```julia
function pickfirst(pipeline, conditioner)
```

Return a copy of the first conditioner of the `pipeline` which is of  the same type as `conditioner`. If no such conditioner is found, return `nothing`. Note that a copy is returned, not the conditioner in the pipeline itself.

The provided `conditioner` can be a type or an instance of a conditioner. The returned element will always be an instance, as pipelines holds instances only.

**See**: [`includes`](@ref)

**Examples**

```julia
using PosDefManifoldML

pipeline = @→ Recenter() Shrink()
S = pickfirst(pipeline, Shrink) 
S isa Conditioner # true
S isa Shrink # true

# retrive a parameter of the conditioner
pickfirst(pipeline, Shrink).radius

```
