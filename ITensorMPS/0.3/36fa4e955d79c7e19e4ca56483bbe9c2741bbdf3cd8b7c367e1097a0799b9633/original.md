```
ITensors.set_ortho_lims!(::MPS/MPO, r::UnitRange{Int})
```

Sets the range of sites of the orthogonality center of the MPS/MPO.

This is not exported and is an advanced feature that should be used with care. Setting the orthogonality limits wrong can lead to incorrect results when using ITensor MPS/MPO functions.

If you are modifying an MPS/MPO and want the orthogonality limits to be preserved, please see the `@preserve_ortho` macro.
