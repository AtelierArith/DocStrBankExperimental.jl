```
EC_from_FCI(Norb_in, Nocc_in; target_dirs="eigenstates_fullCI", gvals_specified::Vector{Float64} = Vector{Float64}[], gvals_target=collect(-2.0:0.1:2.0), degenerate = true, delta_eps::Float64=1.0)
```

Main function to compute the energy curve by EC method from the FCI wavefunctions. Assuming that the FCI wavefunctions are already evaluated and saved in a directory.

# Arguments

  * `Norb_in::Int64`: Number of orbitals.
  * `Nocc_in::Int64`: Number of electrons.
  * `target_dirs::String`: Directory name where the FCI wavefunctions are saved.
  * `gvals_specified::Vector{Float64}`: List of gvals to be used as snapshots. If empty, all the snapshots extracted via `glob` will be used.
  * 
