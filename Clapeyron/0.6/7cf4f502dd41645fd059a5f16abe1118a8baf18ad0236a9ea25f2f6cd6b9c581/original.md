```
shape_factors(model::ECS,V,T,z=SA[1.0])
shape_factors(model::ECS,shape_ref::ABCubicModel,V,T,z=SA[1.0])
shape_factors(model::ECS,shape_ref::EoSModel,V,T,z=SA[1.0])
```

Returns `f` and `h` scaling factors, used by the [`ECS`](@ref) Equation of state.

```
eos(shape_model,v,T,x)/RT = eos(model_ref,v₀,T₀)/RT₀
```

where:

```
T₀ = T/f
v₀ = v/h
```

For cubics, a general procedure is defined in [1]:

```
h = b/b₀
fh = a(T)/a₀(T₀)

```

!!! info "General Shape Factors?"
    For general EoS, there is no existent publications on how to obtain shape factors. However, we can "map" any EoS to a cubic with:

    ```
    b ≈ lb_volume(model,z)
    a ≈ RT*(b - B)
    B = second_virial_coefficient(model,T)
    ```

    This is not tested extensively and it is considered an Experimental feature, subject to future changes.


## References

1. Mollerup, J. (1998). Unification of the two-parameter equation of state and the principle of corresponding states. Fluid Phase Equilibria, 148(1–2), 1–19. [doi:10.1016/s0378-3812(98)00230-1](https://doi.org/10.1016/s0378-3812(98)00230-1)
