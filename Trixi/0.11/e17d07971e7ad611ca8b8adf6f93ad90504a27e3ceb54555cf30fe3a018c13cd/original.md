```
initial_condition_density_wave(x, t, equations::CompressibleEulerEquations2D)
```

A sine wave in the density with constant velocity and pressure; reduces the compressible Euler equations to the linear advection equations. This setup is the test case for stability of EC fluxes from paper

  * Gregor J. Gassner, Magnus Svärd, Florian J. Hindenlang (2020) Stability issues of entropy-stable and/or split-form high-order schemes [arXiv: 2007.09026](https://arxiv.org/abs/2007.09026)

with the following parameters

  * domain [-1, 1]
  * mesh = 4x4
  * polydeg = 5
