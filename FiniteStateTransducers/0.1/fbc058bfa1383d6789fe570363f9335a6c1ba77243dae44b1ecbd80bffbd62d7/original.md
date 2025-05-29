`WFST(isym, [osym]; W = TropicalWeight{Float32})`

Construct an empty Weighted Finite State Transducer (WFST)

  * `isym` input symbol table (can be a dictionary or a vector)
  * `osym` output symbol dictionary (optional)
  * `W` weight type

If the symbol table are `AbstractDict{I,D}`, `D` must be an integer and `I` the type of the symbol.
