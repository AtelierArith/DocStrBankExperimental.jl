```
mean(M::Circle{ℂ}, x::AbstractVector[, w::AbstractWeights])
```

Compute the Riemannian [`mean`](@ref mean(M::AbstractManifold, args...)) of `x` of points on the [`Circle`](@ref) $𝕊^1$, represented by complex numbers, i.e. embedded in the complex plane. Comuting the sum

$$
s = \sum_{i=1}^n x_i
$$

the mean is the angle of the complex number $s$, so represented in the complex plane as $\frac{s}{\lvert s \rvert}$, whenever $s \neq 0$.

If the sum $s=0$, the mean is not unique. For example for opposite points or equally spaced angles.
