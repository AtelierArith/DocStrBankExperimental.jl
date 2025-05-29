```julia
function includes(pipeline, conditioner)
```

Return true if the given [`Pipeline`](@ref) includes a conditioner  of the same type as `conditioner`.

The provided `conditioner` can be a type or an instance of a conditioner.

**See**: [`pickfirst`](@ref), [`@pipeline`](@ref)

**Examples**

```julia
using PosDefManifoldML

pipeline= @→ Recenter() → Shrink()

includes(pipeline, Shrink) # true

includes(pipeline, Shrink()) # true

# same type, althoug a different instance
includes(pipeline, Shrink(Fisher; radius=0.1)) # true

includes(pipeline, Compress) # false
```

**Learn the package**: check out [`saveas`](@ref)
