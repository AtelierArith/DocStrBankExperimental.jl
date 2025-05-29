```julia
struct MomentumMatrix{A<:(AbstractMatrix)}
```

A momentum matrix maps a joint velocity vector to momentum.

This is a slight generalization of the centroidal momentum matrix (Orin, Goswami, "Centroidal momentum matrix of a humanoid robot: Structure and properties.") in that the matrix (and hence the corresponding total momentum) need not be expressed in a centroidal frame.
