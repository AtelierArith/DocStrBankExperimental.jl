```
ProjectedEnergy(hamiltonian, projector; hproj=:hproj, vproj=:vproj) <: PostStepStrategy
```

After every step, compute `hproj = dot(projector, hamiltonian, dv)` and `vproj = dot(projector, dv)`, where `dv` is the instantaneous coefficient vector.  `projector` can be an [`AbstractDVec`](@ref), or an [`AbstractProjector`](@ref).

Reports to columns `hproj` and `vproj`, which can be used to compute projective energy, e.g. with [`projected_energy`](@ref). The keyword arguments `hproj` and `vproj` can be used to change the names of these columns. This can be used to make the names unique when computing projected energies with different projectors in the same run.

See also [`projected_energy`](@ref), [`ratio_of_means`](@ref), [`mixed_estimator`](@ref), and [`PostStepStrategy`](@ref).
