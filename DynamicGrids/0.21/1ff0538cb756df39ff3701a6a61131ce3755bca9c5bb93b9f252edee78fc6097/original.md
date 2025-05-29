```
Aux <: ParameterSource

Aux{K}()
Aux(K::Symbol)
```

Use auxilary array with key `K` as a parameter source.

Implemented in rules with:

```julia
get(data, rule.myparam, I)
```

When an `Aux` param is specified at rule construction with:

```julia
rule = SomeRule(; myparam=Aux{:myaux})
output = ArrayOutput(init; aux=(myaux=myauxarray,))
```

If the array is a DimensionalData.jl `DimArray` with a `Ti` (time) dimension, the correct interval will be selected automatically, precalculated for each timestep so it has no significant overhead.

Currently this is cycled by default. Note that cycling may be incorrect when the simulation timestep (e.g. `Week`) does not fit equally into the length of the time dimension (e.g. `Year`). This will reuire a `Cyclic` index mode in DimensionalData.jl in future to correct this problem.
