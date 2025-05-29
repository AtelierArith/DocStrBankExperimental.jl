```
isoinvset_information(lc::LefschetzComplex, mvf::CellSubsets, iis::Cells)
```

Compute basic information about an isolated invariant set.

The input argument `lc` contains the Lefschetz complex, and `mvf` describes the multivector field. The isolated invariant set is specified in the  argument `iis`. The function returns the information in the form of a `Dict{String,Any}`. The command `keys` can be used to see the keyset of the return dictionary. These describe the following information:

  * `"Conley index"` contains the Conley index of the  isolated invariant set.
  * `"N multivectors"` contains the number of multivectors in the isolated invariant set.
