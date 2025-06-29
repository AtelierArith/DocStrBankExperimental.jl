```
tidal_heating(pnsystem)
```

Compute the rate of energy and angular-momentum absorption into each black hole in a binary.

The returned quantity is a tuple `(Ṡ₁, Ṁ₁, Ṡ₂, Ṁ₂)`, representing the corresponding rates of change of spin (magnitude) and mass on black hole 1 and black hole 2.  These apply to general — possibly precessing — non-eccentric binaries.  This collection of terms comes from [Alvi (2001)](https://doi.org/10.1103/PhysRevD.64.104020).  It probably wouldn't be too hard to extend Alvi's analysis to eccentric systems.

Note that the validity of the result depends not only on the PN parameter $v$, but also on the angles of the spins relative to the separation vector $n̂$: the smaller the angle, the lower the $v$ at which the approximations should be expected to break down.

See also

  * [Tagoshi and Sasaki (1994)](http://arxiv.org/abs/gr-qc/9405062)
  * [Poisson and Sasaki (1995)](https://arxiv.org/abs/gr-qc/9412027)
  * [Tagoshi et al. (1997)](https://arxiv.org/abs/gr-qc/9711072)
  * [Porto (2007)](https://arxiv.org/abs/0710.5150)
  * [Chatziioannou et al. (2012)](https://arxiv.org/abs/1211.1686)

See the documentation section on ["Horizons"](@ref Horizons) for details about the computation of horizon quantities used in this function.
