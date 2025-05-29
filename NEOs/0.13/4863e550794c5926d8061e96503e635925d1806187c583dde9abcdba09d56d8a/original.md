```
RNp1BP_pN_A_J23E_J2S_ng_eph_threads!(dq, q, params, t)
```

Near-Earth asteroid dynamical model ($d = 2$). Bodies considered in the model are: the Sun, the eight planets, the Moon and Ceres, as well as the asteroid of interest as a test particle with null mass. Dynamical effects considered are:

  * Post-Newtonian point-mass accelerations between all bodies: see equation (35) in page 7 of https://ui.adsabs.harvard.edu/abs/1971mfdo.book.....M/abstract.
  * Figure-effects (oblateness) of the Earth ($J_2$ and $J_3$),
  * $J_2$ effect of the Sun and
  * $J_2$ and $J_3$ effect of the Moon: see equation (28) in page 13 of https://ui.adsabs.harvard.edu/abs/2014IPNPR.196C...1F%2F/abstract and equations (173) and (174) in page 33 of https://ui.adsabs.harvard.edu/abs/1971mfdo.book.....M/abstract.
  * Kinematic model for the precession and nutation of the Earth's orientation (IAU 1976/1980 Earth orientation model): see [`PlanetaryEphemeris.c2t_jpl_de430`](@ref).
  * Kinematic model for the Moon's orientation (Seidelmann et al., 2006): see equations (14)-(15) in page 9 and equations (34)-(35) in page 16 of https://ui.adsabs.harvard.edu/abs/2014IPNPR.196C...1F%2F/abstract.
  * Non-gravitational accelerations acting upon the asteroid: are included (Yarkovsky effect)

$$
\mathbf{a}_\text{nongrav} = A_2\left(\frac{1 \ \text{au}}{r}\right)^d*\hat{\mathbf{t}},
$$

where $\hat{\mathbf{t}}$ is the unit heliocentric transverse vector, $r$ is the asteroid's heliocentric range, $A_2$ is a coefficient (with units of au/day^2), and $d = 2$.

To improve performance, some internal loops are multi-threaded via `Threads.threads for`

See also [`PlanetaryEphemeris.NBP_pN_A_J23E_J23M_J2S!`](@ref).
