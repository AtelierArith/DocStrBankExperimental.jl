```
connection_matrix(lc::LefschetzComplex, mvf::CellSubsets;
                  [returnbasis::Bool])
```

Compute a connection matrix for the multivector field `mvf` on the Lefschetz complex `lc` over the field associated with the Lefschetz complex boundary matrix.

The function returns an object of type `ConleyMorseCM`. If the optional argument `returnbasis::Bool=true` is given, then the function also returns a dictionary which gives the basis for the connection matrix columns in terms of the original labels.
