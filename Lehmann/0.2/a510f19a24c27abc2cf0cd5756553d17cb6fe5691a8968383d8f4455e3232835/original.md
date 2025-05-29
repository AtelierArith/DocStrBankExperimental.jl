```
function dlr2tau(dlrGrid::DLRGrid, dlrcoeff, τGrid = dlrGrid.τ; axis = 1, verbose = true)
```

DLR representation to imaginary-time representation

#Members:

  * `dlrGrid`  : DLRGrid
  * `dlrcoeff` : DLR coefficients
  * `τGrid`    : expected fine imaginary-time grids
  * `axis`     : imaginary-time axis in the data `dlrcoeff`
  * `verbose`  : true to print warning information
