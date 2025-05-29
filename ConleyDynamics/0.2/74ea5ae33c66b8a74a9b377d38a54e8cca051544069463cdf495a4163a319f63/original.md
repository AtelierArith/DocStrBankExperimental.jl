```
morse_interval(lc::LefschetzComplex, mvf::CellSubsets,
               ms::CellSubsets)
```

Find the isolated invariant set for a Morse set interval.

The input argument `lc` contains the Lefschetz complex, and `mvf` describes the multivector field. The collection of Morse sets are contained in`ms`. All of these sets should be Morse sets in the sense of being strongly connected components of the flow graph. (Nevertheless, this will be enforced in the function!) In other words, the sets in `ms` should be determined using the function `morse_sets`!

The function returns the smallest isolated invariant set which contains the Morse sets and their connections as a `Vector{Int}`.
