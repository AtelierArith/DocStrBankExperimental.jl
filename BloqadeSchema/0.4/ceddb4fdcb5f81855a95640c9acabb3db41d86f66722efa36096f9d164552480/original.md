```
struct HardwareTransformInfo <: QuEraSchema
```

Contains the calculated differences (error) betwen the original and transformed waveforms and atoms from invoking [`hardware_transform`](@ref) on a [`BloqadeExpr.RydbergHamiltonian`](@ref).

# Fields

  * `ϕ_error`: Error between the original laser phase waveform ($A$) and transformed one ($B$) waveforms calculated as $\Vert A - B\Vert_1$.
  * `Ω_error`: Error between the original Rabi frequency waveform ($A$) and transformed one ($B$) waveforms calculated as $\Vert A - B\Vert_1$.
  * `Δ_error`: Error between the global detuning waveform ($A$) and transformed one ($B$) waveforms calculated as $\Vert A - B\Vert_1$.
  * `Δ_mask`: Decoupling of local detuning field inferred from the detuning value specified in Δ.

!!! note "Local Detuning Support"
    Local Detunings are currently not supported by Bloqade but will be in future releases.


  * `mse_atoms`: Mean Squared Error between original atom positions and transformed ones.
