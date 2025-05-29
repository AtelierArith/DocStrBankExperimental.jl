```
conformal_cubed_sphere_mapping(x, y; W_map=W_Rancic)
```

Conformal mapping from a face of a cube onto the equivalent sector of a sphere with unit radius.

Map the north-pole face of a cube with coordinates $(x, y)$ onto the equivalent sector of the sphere with coordinates $(X, Y, Z)$.

The cube's face oriented normal to $z$-axis and its coordinates must lie within the range $-1 ≤ x ≤ 1$, $-1 ≤ y ≤ 1$ with its center at $(x, y) = (0, 0)$. The coordinates $X, Y$ increase in the same direction as $x, y$.

The numerical conformal mapping used here is described by [Rancic-etal-1996](@citet).

This is a Julia translation of [MATLAB code from MITgcm](http://wwwcvs.mitgcm.org/viewvc/MITgcm/MITgcm_contrib/high_res_cube/matlab-grid-generator/map_xy2xyz.m?view=markup) that is based on Fortran 77 code from Jim Purser & Misha Rančić.

# Examples

The center of the cube's face $(x, y) = (0, 0)$ is mapped onto $(X, Y, Z) = (0, 0, 1)$

```jldoctest
julia> using CubedSphere

julia> conformal_cubed_sphere_mapping(0, 0)
(0, 0, 1.0)
```

and the edge of the cube's face at $(x, y) = (1, 1)$ is mapped onto $(X, Y, Z) = (√3/3, √3/3, √3/3)$

```jldoctest
julia> using CubedSphere

julia> conformal_cubed_sphere_mapping(1, 1)
(0.5773502691896256, 0.5773502691896256, 0.5773502691896257)
```

# References

  * [Rancic-etal-1996](@cite) Rančić et al., *Q. J. R. Meteorol.*, (1996).
