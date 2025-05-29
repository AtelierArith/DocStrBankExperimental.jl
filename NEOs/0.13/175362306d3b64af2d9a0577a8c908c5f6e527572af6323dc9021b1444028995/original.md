```
valsecchi_circle(a, e, i, k, h; m_pl=3.003489614915764e-6)
```

Computes Valsecchi circle associated to a mean motion resonance. Returns radius $R$ (au) and $\zeta$-axis coordinate $D$ (au). This function first computes the Y-component and norm of the planetocentric velocity vector $\mathbf{U}$

$$
U_y = \sqrt{a(1-e^2)}\cos i - 1 \quad \text{and} \quad
U = ||\mathbf{U}|| = \sqrt{3 - \frac{1}{a} - 2\sqrt{a(1-e^2)}\cos i},
$$

and then substitutes into `valsecchi_circle(U_y, U_norm, k, h; m_pl=3.003489614915764e-6, a_pl=1.0)`. `a`, `e` and `i` are the asteroid heliocentric semimajor axis (au), eccentricity and inclination (rad) respectively.

# Arguments

  * `a`: asteroid heliocentric semimajor axis (au).
  * `e`: asteroid heliocentric eccentricity.
  * `i`: asteroid heliocentric inclination, ecliptic (rad).
  * `k/h`: `h` heliocentric revolutions of asteroid per `k` heliocentric revolutions of Earth.
  * `m_pl`: planet mass normalized to Sun's mass, equal to Earth mass in solar masses by default.

!!! reference
    See section 2.1 in page 1181 of https://doi.org/10.1051/0004-6361:20031039.

