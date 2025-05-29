```
function krylov_extend!(engine::TDVPEngine{ProjMPO}; kwargs...)
```

Performs Global Subspace Expansion.

#### Arguments and their default values:

  * `extension_krylovdim::Int = 3`: Number of Krylov vectors used for GSE.
  * `extension_applyH_cutoff::Float64 = Float64_threshold()`: Cutoff for the application the MPO to the MPS.
  * `extension_applyH_maxdim::Int = maxlinkdim(psi) + 1`: Maximum bond/link dimension of the resulting MPS after the application of the MPO to the MPS.
  * `extension_cutoff::Float64 = 1E-10`: Cutoff for the basis extension step in GSE.
