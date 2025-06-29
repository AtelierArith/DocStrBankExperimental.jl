```
distance(q₁, q₂)
distance2(q₁, q₂)
```

Measure the "distance" between two quaternions, or the squared distance with `distance2`.

By default, this function just returns the natural measure in the *additive* group of quaternions:

```julia
abs2(q₁ - q₂)
```

If both arguments are `Rotor`s, the function returns the natural measure in the *rotation* group, which is roughly

```julia
abs2(log(q₁ / q₂))
```

Note that for `Rotor`s, this method is (efficiently) independent of the scaling of `q₁` and `q₂`, including up to factors of -1, as is appropriate for the rotation group.

# Examples

```jldoctest example
julia> distance(imx, imy)
1.4142135623730951
julia> distance(rotor(imx), rotor(imy))
1.5707963267948966
julia> distance(imz, -imz)
2.0
julia> distance(rotor(imz), rotor(-imz))
0.0
```
