```
mvf_information(lc::LefschetzComplex, mvf::CellSubsets)
```

Extract basic information about a multivector field.

The input argument `lc` contains the Lefschetz complex, and `mvf` describes the multivector field. The function returns the information in the form of a `Dict{String,Any}`. You can use the command `keys` to see the keyset of the return dictionary:

  * `"N mv"`: Number of multivectors
  * `"N critical"`: Number of critcal multivectors
  * `"N regular"`: Number of regular multivectors
  * `"Lengths critical"`: Length distribution of critical multivectors
  * `"Lengths regular"`: Length distribution of regular multivectors

In the last two cases, the dictionary entries are vectors of pairs `(length,frequency)`, where each pair indicates that there are `frequency` multivectors of length `length`.
