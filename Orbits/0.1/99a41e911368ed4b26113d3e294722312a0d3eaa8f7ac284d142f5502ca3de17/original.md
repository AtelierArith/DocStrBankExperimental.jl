```
KeplerianOrbit(; kwargs...)
```

Keplerian orbit parameterized by the basic observables of a transiting 2-body system.

# Parameters

  * `period`/`P` – The orbital period of the planet [d].
  * `t0`/`t_0` – The midpoint time of the reference transit [d].
  * `tp`/`t_p` – The time of periastron [d].
  * `duration`/`τ`/`T` – The transit duration [d].
  * `a` – The semi-major axis [R⊙].
  * `aR_star`/`aRs` – The ratio of the semi-major axis to star radius.
  * `R_planet`/`Rp` – The radius of the planet [R⊙].
  * `R_star`/`Rs` – The radius of the star [R⊙].
  * `rho_star`/`ρ_star` – The spherical star density [M⊙/R⊙³].
  * `r`/`RpRs` – The ratio of the planet radius to star radius.
  * `b` – The impact parameter, bounded between 0 ≤ b ≤ 1.
  * `ecc`/`e` – The eccentricity of the closed orbit, bounded between 0 ≤ ecc < 1.
  * `incl` – The inclination of the orbital plane relative to the axis perpendicular to the          reference plane [rad]
  * `omega`/`ω` – The argument of periapsis [rad].
  * `cos_omega`/`cos_ω` – The cosine of the argument of periapsis.
  * `sin_omega`/`sin_ω` – The sine of the argument of periapsis.
  * `Omega`/`Ω` – The longitude of the ascending node [rad].
  * `M_planet`/`Mp` – The mass of the planet [M⊙].
  * `M_star`/`Ms` – The mass of the star [M⊙].

# Valid combinations

The following flowchart can be used to determine which parameters can define a `KeplerianOrbit`:

1. The `period` or `a` must be given. If both given, then neither `M_star` or `rho_star` can be defined because the stellar density is now implied.
2. Only `incl` or `b` can be given.
3. If `ecc` is given, then `omega` must also be given.
4. If no stellar parameters are given, the central body is assumed to be the Sun. If only `rho_star` is given, then `R_star` is defined to be 1 solar radius. Otherwise, at most two of `M_star`, `R_star`, and `rho_star` can be given.
5. Either `t0` or `tp` must be given, but not both.
