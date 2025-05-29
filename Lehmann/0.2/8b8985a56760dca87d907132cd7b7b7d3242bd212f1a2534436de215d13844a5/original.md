```
function DLRGrid(Euv, β, rtol, isFermi::Bool; symmetry::Symbol = :none, rebuild = false, folder = nothing, algorithm = :functional, verbose = false)
function DLRGrid(; isFermi::Bool, β = -1.0, beta = -1.0, Euv = 1.0, symmetry::Symbol = :none, rtol = 1e-14, rebuild = false, folder = nothing, algorithm = :functional, verbose = false)
```

Create DLR grids

#Arguments:

  * `Euv`         : the UV energy scale of the spectral density
  * `β` or `beta` : inverse temeprature
  * `isFermi`     : bool is fermionic or bosonic
  * `symmetry`    : particle-hole symmetric :ph, or particle-hole asymmetric :pha, or :none
  * `rtol`        : tolerance absolute error
  * `rebuild`     : set false to load DLR basis from the file, set true to recalculate the DLR basis on the fly
  * `folder`      : if rebuild is true and folder is set, then dlrGrid will be rebuilt and saved to the specified folder                   if rebuild is false and folder is set, then dlrGrid will be loaded from the specified folder
  * `algorithm`   : if rebuild = true, then set :functional to use the functional algorithm to generate the DLR basis, or set :discrete to use the matrix algorithm.
  * `verbose`     : false not to print DLRGrid to terminal, or true to print
