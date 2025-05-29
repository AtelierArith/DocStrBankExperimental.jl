According to Eq. (5.42) – Eq. (5.44) in Mishchenko et al. (2002), the T-Matrix for a Mie particle can be written as:

$$
\begin{array}{l}
T_{m n m^{\prime} n^{\prime}}^{12}(P) \equiv 0, \quad T_{m n m^{\prime} n^{\prime}}^{21}(P) \equiv 0, \\
T_{m n m^{\prime} n^{\prime}}^{11}(P)=-\delta_{m m^{\prime}} \delta_{n n^{\prime}} b_n, \\
T_{m n m^{\prime} n^{\prime}}^{22}(P)=-\delta_{m m^{\prime}} \delta_{n n^{\prime}} a_n .
\end{array}
$$

```
MieTransitionMatrix{CT, N}(x::Real, m::Number)
```

Generate the T-Matrix from the Mie coefficients of a homogeneous sphere.

```
MieTransitionMatrix{CT, N}(x_core::Real, x_mantle::Real, m_core::Number, m_mantle::Number)
```

Generate the T-Matrix from the Mie coefficients of a coated sphere.

This struct provides the T-Matrix API for a Mie particle.
