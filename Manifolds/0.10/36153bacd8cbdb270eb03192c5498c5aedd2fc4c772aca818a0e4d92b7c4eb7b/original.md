```
apply(A::RotationAroundAxisAction, θ, p)
```

Rotate point `p` from [`Euclidean(3)`](@ref) manifold around axis `A.axis` by angle `θ`. The formula reads

$$
p_{rot} = (\cos(θ))p + (k×p) \sin(θ) + k (k⋅p) (1-\cos(θ)),
$$

where $k$ is the vector `A.axis` and `⋅` is the dot product.
