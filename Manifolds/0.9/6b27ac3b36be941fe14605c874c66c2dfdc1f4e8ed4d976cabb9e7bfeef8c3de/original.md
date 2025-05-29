```
Circle{𝔽} <: AbstractManifold{𝔽}
```

The circle $𝕊^1$ is a manifold here represented by real-valued points in $[-π,π)$ or complex-valued points $z ∈ ℂ$ of absolute value $\lvert z\rvert = 1$.

# Constructor

```
Circle(𝔽=ℝ)
```

Generate the `ℝ`-valued Circle represented by angles, which alternatively can be set to use the [`AbstractNumbers`](@extref ManifoldsBase number-system) `𝔽=ℂ` to obtain the circle represented by `ℂ`-valued circle of unit numbers.
