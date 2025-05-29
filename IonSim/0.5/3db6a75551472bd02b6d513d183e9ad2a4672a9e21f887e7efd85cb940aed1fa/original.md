```
VibrationalMode(
        ν::Real, modestructure::Vector{Real}, δν::Union{Function,Real}=0.; N::Int=10,
        axis::NamedTuple{(:x,:y,:z)}=ẑ
    )
```

**user-defined fields**

  * `ν::Real`: frequency [Hz]
  * `modestructure::Vector{Real}`: The normalized eigenvector describing the collective motion        of the ions belonging to this mode.
  * `δν::Union{Function,Real}`: Either a function describing time-dependent fluctuations of `ν`       or a real number which will be converted to the constant function `t -> δν`.
  * `N::Int`: Highest level included in the Hilbert space.
  * `axis::NamedTuple{(:x,:y,:z)}`: The axis of symmetry for the vibration. This must lie along       one of the basis vectors `x̂`, `ŷ` or `ẑ`.

**derived fields**

  * `shape::Vector{Int}`: Indicates dimension of used Hilbert space (`=[N+1]`).
  * `_cnst_δν::Bool`: A Boolean flag signifying whether or not `δν` is a constant function.

Note: the iᵗʰ Fock state (|i⟩) can be obtained by indexing as `v=VibrationalMode(...); v[i]`
