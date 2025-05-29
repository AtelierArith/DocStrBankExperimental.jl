```
BlendedGradientCorrection()
```

Calculate a blended gradient to reduce the stability issues of the [`GradientCorrection`](@ref) as explained by [Bonet (1999)](@cite Bonet1999).

This calculates the following,

$$
\tilde\nabla A_i = (1-\lambda) \nabla A_i + \lambda L_i \nabla A_i
$$

with $0 \leq \lambda \leq 1$ being the blending factor.

# Arguments

  * `blending_factor`: Blending factor between corrected and regular SPH gradient.
