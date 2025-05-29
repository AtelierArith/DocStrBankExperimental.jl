```
spincube = mSpinCube(dim::Dims{3}, fov; ofst, Δf, T1, T2, γ)
spincube = mSpinCube(mask::BitArray{3}, fov; ofst, Δf, T1, T2, γ)
```

`dim`, `mask`, `T1`, `T2`, and `γ` are passed to `mSpinArray` constructors.

An exemplary struct instantiating `AbstractSpinCube`, designed to model a set of regularly spaced spins, e.g., a volume.

# Fields:

*Immutable*:

  * `spinarray::AbstractSpinArray` (1,): inherited `AbstractSpinArray` struct
  * `fov ::TypeND(L0D, [2])` (1, 3): field of view.
  * `ofst::TypeND(L0D, [2])` (1, 3): fov offset from magnetic field iso-center.
  * `loc ::TypeND(L0D, [2])` (nM, 3): location of spins.

*Mutable*:

  * `Δf::TypeND(F0D, [0,1])` (1,) or (nM,): off-resonance map.

See also: [`AbstractSpinCube`](@ref).
