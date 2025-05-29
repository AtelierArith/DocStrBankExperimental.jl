```
VolumeIntegralPureLGLFiniteVolume(volume_flux_fv)
```

A volume integral that only uses the subcell finite volume schemes of the [`VolumeIntegralShockCapturingHG`](@ref).

This gives a formally O(1)-accurate finite volume scheme on an LGL-type subcell mesh (LGL = Legendre-Gauss-Lobatto).

!!! warning "Experimental implementation"
    This is an experimental feature and may change in future releases.


## References

  * Hennemann, Gassner (2020) "A provably entropy stable subcell shock capturing approach for high order split form DG" [arXiv: 2008.12044](https://arxiv.org/abs/2008.12044)
