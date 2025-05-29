```
conformal_cubed_sphere_inverse_mapping(X, Y, Z; Z_map=Z_Rancic)
```

Inverse mapping for conformal cube sphere for quadrant of North-pole face in which `X` and `Y` are both positive. All other mappings to other cube face coordinates can be recovered from rotations of this map. There a 3 other quadrants for the north-pole face and five other faces for a total of twenty-four quadrants. Because of symmetry only the reverse for a single quadrant is needed. Because of branch cuts and the complex transform the inverse mappings are multi-valued in general, using a single quadrant case allows a simple set of rules to be applied.

The mapping is valid for the cube face quadrant defined by $0 < x < 1$ and $0 < y < 1$, where a full cube face has extent $-1 < x < 1$ and $-1 < y < 1$. The quadrant for the mapping is from a cube face that has "north-pole" at its center $(x=0, y=0)$. i.e., has `X, Y, Z = (0, 0, 1)` at its center. The valid ranges of `X` and `Y` for this mapping and convention are a quadrant defined be geodesics that connect the points A, B, C and D, on the shell of a sphere of radius $R$ with `X`, `Y` coordinates as follows

```
A = (0, 0)
B = (√2, 0)
C = (√3/3, √3/3)
D = (0, √2)
```
