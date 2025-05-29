```
comoving_radial_dist([u::Unitlike,] c::AbstractCosmology, [z₁,] z₂)
```

Comoving radial distance ($D_C$) in Mpc at redshift `z₂` as seen by an observer at `z₁`. Redshift `z₁` defaults to 0 if omitted.  Will convert to compatible unit `u` if provided.

It's calculated as $D_C = D_{H0} Z$, where $D_{H0}$ is the Hubble distance at the present epoch and, $Z = \int_{z_1}^{z_2} \frac{dz}{E(z)}$.
