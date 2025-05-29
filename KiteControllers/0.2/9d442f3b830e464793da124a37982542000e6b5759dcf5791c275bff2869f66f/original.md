```
on_est_sysstate(fpc, phi, beta, psi, chi, omega, v_a; u_d=nothing, u_d_prime=nothing)
```

Parameters:

  * phi:      azimuth angle of the kite position in radian
  * beta:     elevation angle of the kite position in radian
  * psi:      heading of the kite in radian
  * chi:      course of the kite in radian
  * omega:    angular velocity of the kite on the unit sphere in degrees/s ???
  * u_d:      depower settings             [0..1]
  * u*d*prime normalized depower settings  [0..1]

Either u*d or u*d_prime must be provided.
