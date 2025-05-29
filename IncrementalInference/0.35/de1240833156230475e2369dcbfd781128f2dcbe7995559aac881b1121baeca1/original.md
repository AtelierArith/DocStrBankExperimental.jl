```julia
cont2disc(F, G, Qc, dt)
cont2disc(F, G, Qc, dt, Phik)

```

Standard mean and covariance propagation for linear systems.  Directly equivalent to Kalman filtering methods.

Notes

  * Does the proper continuous (Qc) to discrete process noise (Qd) calculation – as per Farrell, 2008.
  * Used downstream for in-time Gaussian mean and covariance propagation.
