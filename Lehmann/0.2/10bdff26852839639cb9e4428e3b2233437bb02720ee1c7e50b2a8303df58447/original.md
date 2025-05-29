```
function tau2dlr(dlrGrid::DLRGrid, green, τGrid = dlrGrid.τ; error = nothing, axis = 1, sumrule = nothing, verbose = true)
```

imaginary-time domain to DLR representation

#Members:

  * `dlrGrid`  : DLRGrid struct.
  * `green`    : green's function in imaginary-time domain.
  * `τGrid`    : the imaginary-time grid that Green's function is defined on.
  * `error`    : error the Green's function.
  * `axis`     : the imaginary-time axis in the data `green`.
  * `sumrule`  : enforce the sum rule
  * `verbose`  : true to print warning information
