```
dxy_dt_replay(du,u,p::DataFrame,t)
```

Interpolate velocity from MITgcm float_trajectories output and return position increment `du`.

# Extended help

```jldoctest; output = false
using IndividualDisplacements
p=dirname(pathof(IndividualDisplacements))
include(joinpath(p,"../examples/more/detailed_look.jl"))
prod(isapprox.(sol[:,end],ref[:,end],atol=1.0))

# output

true
```
