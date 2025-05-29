```
MapSliceOp(trafo, dim::Int64, size1::Tuple, size2::Tuple; T=ComplexF64)
```

generates an operator that applies `trafo` to each slice of dimension `dim` of an array

# Arguments

  * `trafo`           - transformation to apply
  * `size1`           - size of the Array to be transformed
  * `size2`           - size of the resulting Array of applying trafo to all slices
  * (`T=ComplexF64`)  - type of the transformation
