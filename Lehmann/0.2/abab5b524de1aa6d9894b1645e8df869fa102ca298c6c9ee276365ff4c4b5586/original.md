```
function matfreq2tau(dlrGrid, green, τNewGrid = dlrGrid.τ, nGrid = dlrGrid.n; error = nothing, axis = 1, sumrule = nothing, verbose = true)
```

Fourier transform from Matsubara-frequency to imaginary-time using the DLR representation

#Members:

  * `dlrGrid`  : DLRGrid
  * `green`    : green's function in Matsubara-freqeuncy repsentation
  * `τNewGrid` : expected fine imaginary-time grids
  * `nGrid`    : the n grid that Green's function is defined on.
  * `error`    : error the Green's function.
  * `axis`     : Matsubara-frequency axis in the data `green`
  * `sumrule`  : enforce the sum rule
  * `verbose`  : true to print warning information
