```
dxy_dt_CyclicArray(du,u,P::NamedTuple,tim)
```

Nearest neighbor (?) velocity from gridded fields (2D; NO halos but not needed when CyclicArrays is used to extend valid indice ranges).

# Extended help

*notes:* spatial interpolation & temporal interpolation are lacking

```jldoctest; output = false
using IndividualDisplacements
p=dirname(pathof(IndividualDisplacements))
include(joinpath(p,"../examples/more/example_CyclicArray.jl"))
(x,y)=cyclicarray_example()

ref=[330.5 290.5]
prod(isapprox.([x[end] y[end]],ref,atol=1.0))

# output

true
```
