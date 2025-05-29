# Actin rings dynamics simulation package

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.7781755.svg)](https://doi.org/10.5281/zenodo.7781755)

A Julia package for simulating the dynamics of passively crosslinked actin rings.

[Repository](https://github.com/cumberworth/ActinFriction.jl)

[Documentation](http://www.cumberworth.org/ActinFriction.jl)

This package allows the SDEs described in [Ref. 1](#references) to be solved, and provides methods for directly calculating the friction coefficients described in the same paper.

## Installation

The package can be installed by starting the Julia REPL, typing `]` to enter package mode, and running

```
add ActinFriction
```

to install from the General registry, or by running

```
add https://github.com/cumberworth/ActinFriction.jl
```

to install directly from the development repository.

A related python package, [actinfrictionpy](https://github.com/cumberworth/actinfrictionpy), includes code for analyzing and plotting the output from these ...

## References

[1] A. Cumberworth and P. R. ten Wolde, Constriction of actin rings by passive crosslinkers, [arXiv:2203.04260 [physics.bio-ph]](https://doi.org/10.48550/arXiv.2203.04260).

## Links

[Julia programming language](https://julialang.org/)

[Plotting package](https://github.com/cumberworth/actinfrictionpy)

[Replication package Ref. 1](https://doi.org/10.5281/zenodo.6327217)

  * [`R_to_lambda`](@ref)
  * [`RingParams`](@ref)
  * [`bending_force`](@ref)
  * [`condensation_force`](@ref)
  * [`entropic_force`](@ref)
  * [`equilibrium_occupancy`](@ref)
  * [`equilibrium_ring_radius`](@ref)
  * [`force_L_to_R`](@ref)
  * [`free_energy_barrier_Nd_exact`](@ref)
  * [`free_energy_barrier_Nd_exp`](@ref)
  * [`free_energy_barrier_cX`](@ref)
  * [`friction_coefficient_Nd_exact`](@ref)
  * [`friction_coefficient_Nd_exp`](@ref)
  * [`friction_coefficient_cX`](@ref)
  * [`kramers_r0`](@ref)
  * [`l_to_lambda`](@ref)
  * [`lambda_to_R`](@ref)
  * [`lambda_to_l`](@ref)
  * [`savename`](@ref)
  * [`solve_and_write_ring_Nd_contin_exp`](@ref)
  * [`solve_and_write_ring_Nd_contin_exp_noise`](@ref)
  * [`solve_and_write_ring_Nd_discrete_exact`](@ref)
  * [`solve_and_write_ring_Nd_discrete_exact_noise`](@ref)
  * [`solve_and_write_ring_Nd_discrete_exp`](@ref)
  * [`solve_and_write_ring_Nd_discrete_exp_noise`](@ref)
  * [`solve_and_write_ring_cX`](@ref)
  * [`solve_and_write_ring_cX_noise`](@ref)
