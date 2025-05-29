```
PairingHamiltonian(to; Norb_in::Int=8, Nocc_in::Int=4, gval::Float64=0.33, delta_eps::Float64=1.0,
                    debug_mode::Int=0, solver::String="FCI(2-fold)", save_Exact_wf::Bool=false)
```

Main function to evaluate the ground state energy of the pairing Hamiltonian.

# Optional arguments with default values

  * `Norb_in::Int=8`: number of orbitals
  * `Nocc_in::Int=4`: number of occupied states
  * `gval::Float64=0.33`: pairing strength
  * `delta_eps::Float64=1.0`: energy difference between orbitals
  * `debug_mode::Int=0`: specify the debug mode
  * `solver::String("FCI(2-fold)")`: method to solve the Hamiltonian. This can be one of "Full-CI", "Full-CI(2-fold)", "HF", "BCS", "CCD", "IMSRG(2)". If "HF" is chosen, PT2/PT3 energies are also calculated.
  * `save_Exact_wf::Bool(false)`: save the full-CI wave functions as HDF5 files, which can be used for e.g. analysis of the wave functions and constructing surrogate models like eigenvector continuation.
  * `to`: either nothing or TimerOutput object defined in a user script.
