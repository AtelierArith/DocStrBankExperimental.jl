```
get_combined_design(d::Design; diagnostics::Bool = false)
```

Returns a copy of the design `d` where the three parameters describing Pauli X, Y, and Z basis measurements have been combined into a single parameter for each qubit, printing diagnostics if `diagnostics` is `true`.
