```
get_nsteps(basis::WaveguideBasis)
get_nsteps(basis::Basis)
get_nsteps(basis::CompositeBasis)
```

[`WaveguideBasis`](@ref) の nsteps を返します。これは、[`WaveguideBasis`](@ref) または [`WaveguideBasis`](@ref) を含む `CompositeBasis` のいずれかが与えられた場合です。
