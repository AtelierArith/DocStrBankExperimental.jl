```
GradientCorrection()
```

Compute the corrected gradient of particle interactions based on their relative positions (see [Bonet, 1999](@cite Bonet1999)).

# Mathematical Details

Given the standard SPH representation, the gradient of a field $A$ at particle $a$ is given by

$$
\nabla A_a = \sum_b m_b \frac{A_b - A_a}{\rho_b} \nabla_{r_a} W(\Vert r_a - r_b \Vert, h),
$$

where $m_b$ is the mass of particle $b$ and $\rho_b$ is the density of particle $b$.

The gradient correction, as commonly proposed, involves multiplying this gradient with a correction matrix $L$:

$$
\tilde{\nabla} A_a = \bm{L}_a \nabla A_a
$$

The correction matrix  $\bm{L}_a$ is computed based on the provided particle configuration, aiming to make the corrected gradient more accurate, especially near domain boundaries.

To satisfy

$$
\sum_b V_b r_{ba} \otimes \tilde{\nabla}W_b(r_a) = \left( \sum_b V_b r_{ba} \otimes \nabla W_b(r_a) \right) \bm{L}_a^T = \bm{I}
$$

the correction matrix $\bm{L}_a$ is evaluated explicitly as

$$
\bm{L}_a = \left( \sum_b V_b \nabla W_b(r_{a}) \otimes r_{ba} \right)^{-1}.
$$

!!! note
      * Stability issues arise, especially when particles separate into small clusters.
      * Doubles the computational effort.
      * Better stability with smoother smoothing Kernels with larger support, e.g. [`SchoenbergQuinticSplineKernel`](@ref) or [`WendlandC6Kernel`](@ref).
      * Set `dt_max =< 1e-3` for stability.

