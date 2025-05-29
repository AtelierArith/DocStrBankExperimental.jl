```
function matfreq2dlr(dlrGrid::DLRGrid, green, nGrid = dlrGrid.n; error = nothing, axis = 1, sumrule = nothing, verbose = true)
```

Matsubara-frequency representation to DLR representation

#Members:

  * `dlrGrid`  : DLRGrid struct.
  * `green`    : green's function in Matsubara-frequency domain
  * `nGrid`    : the n grid that Green's function is defined on.
  * `error`    : error the Green's function.
  * `axis`     : the Matsubara-frequency axis in the data `green`
  * `sumrule`  : enforce the sum rule
  * `verbose`  : true to print warning information
