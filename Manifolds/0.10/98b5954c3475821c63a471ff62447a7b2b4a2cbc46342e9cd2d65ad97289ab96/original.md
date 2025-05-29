```
apply(A::QuaternionRotation, g::Quaternion, p)
```

Rotate point `p` from [`Euclidean`](@ref)`(3)` manifold through conjugation by the group element `g`. The formula reads

$$
(0, p_{rot,x}, p_{rot,y}, p_{rot,z}) = g ⋅ (0, p_x, p_y, p_z) ⋅ g^{\mathrm{H}}
$$

where $(0, p_x, p_y, p_z)$ is quaternion with non-real coefficients from encoding the point `p` and $g^{\mathrm{H}}$ is quaternion conjugate of $g$.
