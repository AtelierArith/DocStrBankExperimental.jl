```
valsecchi_circle(U_y, U_norm, k, h; m_pl=3.003489614915764e-6, a_pl=1.0)
```

Computes Valsecchi circle associated to a mean motion resonance. Returns radius $R$ (au) and $\zeta$-axis coordinate $D$ (au)

$$
R = \left|\frac{c\sin\theta_0'}{\cos\theta_0' - \cos\theta}\right| \quad \text{and} \quad
D = \frac{c\sin\theta}{\cos\theta_0' - \cos\theta},
$$

where $c = m/U^2$ with $m$ the mass of the planet and $U = ||\mathbf{U}||$ the norm of the planetocentric velocity vector; and $\theta$, $\theta_0'$ are the angles between Y-axis and $\mathbf{U}$ pre and post encounter respectively.

# Arguments

  * `U_y`: Y-component of unperturbed planetocentric velocity (Y-axis coincides with the direction of motion of the planet).
  * `U_norm`: Euclidean norm of unperturbed planetocentric velocity. Both `U_y`, `U_norm` are in units such that the heliocentric velocity of the planet is 1.
  * `k/h`: `h` heliocentric revolutions of asteroid per `k` heliocentric revolutions of Earth.
  * `m_pl`: planet mass normalized to Sun's mass, equal to Earth mass in solar masses by default.
  * `a_pl`: planetary heliocentric semimajor axis in au; default value is 1.

!!! reference
    See pages 1181, 1182 and 1187 of https://doi.org/10.1051/0004-6361:20031039.

