```
function dlr2matfreq(dlrGrid::DLRGrid, dlrcoeff, nGrid = dlrGrid.n; axis = 1, verbose = true)
```

DLR representation to Matsubara-frequency representation

#Members:

  * `dlrGrid`  : DLRGrid
  * `dlrcoeff` : DLR coefficients
  * `nGrid`    : expected fine Matsubara-freqeuncy grids (integer)
  * `axis`     : Matsubara-frequency axis in the data `dlrcoeff`
  * `verbose`  : true to print warning information
