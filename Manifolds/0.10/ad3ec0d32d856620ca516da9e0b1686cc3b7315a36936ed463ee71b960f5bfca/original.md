```
apply(A::ComplexPlanarRotation, g::Complex, p)
```

Rotate point `p` from [`Euclidean(2)`](@ref) manifold by the group element `g`. The formula reads

$$
p_{rot} =  \begin{bmatrix}
\cos(θ) & \sin(θ)\\
-\sin(θ) & \cos(θ)
\end{bmatrix} p,
$$

where `θ` is the argument of complex number `g`.
