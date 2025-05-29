```
function tau2matfreq(dlrGrid, green, nNewGrid = dlrGrid.n, τGrid = dlrGrid.τ; error = nothing, axis = 1, sumrule = nothing, verbose = true)
```

Fourier transform from imaginary-time to Matsubara-frequency using the DLR representation

#Members:

  * `dlrGrid`  : DLRGrid
  * `green`    : green's function in imaginary-time domain
  * `nNewGrid` : expected fine Matsubara-freqeuncy grids (integer)
  * `τGrid`    : the imaginary-time grid that Green's function is defined on.
  * `error`    : error the Green's function.
  * `axis`     : the imaginary-time axis in the data `green`
  * `sumrule`  : enforce the sum rule
  * `verbose`  : true to print warning information
