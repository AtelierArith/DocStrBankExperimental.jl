```
ExtendedCorrespondingStates <: EoSModel

function ECS(components,
    refmodel=PropaneRef(),
    shapemodel=SRK(components),
    shaperef = SRK(refmodel.components))
```

## Input Models

  * `shape_model`: shape model
  * `shape_ref`:  shape reference. is the same type of EoS that `shape_model`
  * `model_ref`: Reference model

## Description

A Extended Corresponding states method.

The idea is to use a "shape model" that provides a corresponding states parameters and a "reference model" that implements a helmholtz energy function, so that:

```
eos(shape_model,v,T,x)/RT = eos(model_ref,v₀,T₀)/RT₀
```

where:

```
T₀ = T/f
v₀ = v/h
f,h = shape_factors(model::ECS,shape_ref::EoSModel,V,T,z)
```

[`shape_factors`](@ref) can be used to create custom Extended Corresponding state models.

## References

.1 Mollerup, J. (1998). Unification of the two-parameter equation of state and the principle of corresponding states. Fluid Phase Equilibria, 148(1–2), 1–19. [doi:10.1016/s0378-3812(98)00230-1](https://doi.org/10.1016/s0378-3812(98)00230-1)
