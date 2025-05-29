```
function tau2tau(dlrGrid, green, τNewGrid, τGrid = dlrGrid.τ; error = nothing, axis = 1, sumrule = nothing, verbose = true)
```

Interpolation from the old imaginary-time grid to a new grid using the DLR representation

#Members:

  * `dlrGrid`  : DLRGrid
  * `green`    : green's function in imaginary-time domain
  * `τNewGrid` : expected fine imaginary-time grids
  * `τGrid`    : the imaginary-time grid that Green's function is defined on.
  * `error`    : error the Green's function.
  * `axis`     : the imaginary-time axis in the data `green`
  * `sumrule`  : enforce the sum rule
  * `verbose`  : true to print warning information
