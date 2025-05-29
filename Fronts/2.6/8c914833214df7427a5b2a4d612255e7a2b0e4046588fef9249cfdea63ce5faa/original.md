```
BoltzmannODE([; b_hint, d_dob_hint])
```

Default algorithm for solving semi-infinite problems.

Uses the Boltzmann transformation and (possibly repeated) ODE integration.

# Keyword arguments

  * `b_hint`: optional hint for the boundary value.
  * `d_dob_hint`: optional hint for the boundary `o`-derivative.

# References

GERLERO, G. S.; BERLI, C. L. A.; KLER, P. A. Open-source high-performance software packages for direct and inverse solving of horizontal capillary flow. Capillarity, 2023, vol. 6, no. 2, p. 31-40.
