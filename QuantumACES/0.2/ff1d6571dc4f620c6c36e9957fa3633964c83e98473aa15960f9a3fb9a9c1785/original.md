```
get_tuple_set_data(c::AbstractCircuit; error_target::Real = 0.1, add_circuit::Bool = false)
get_tuple_set_data(c::AbstractCircuit, tuple_set::Vector{Vector{Int}}; error_target::Real = 0.1, add_circuit::Bool = false)
```

Returns the tuple set data corresponding to the circuit `c`, with the non-repeated tuples either being the supplied `tuple_set` or the basic tuple set for `c`. The repeat numbers are initialised to be inversely proportional to the average noise on the gates in the layers, which heuristically roughly target an error rate `error_target`, and the original circuit is added to the repeat tuples if `add_circuit` is `true`.

Note that it appears best to use repeat tuples of order 2 (up to Paulis), with odd repeat numbers where this is efficient for measurement (such as repeating the same circuit layer many times), and even repeat numbers otherwise (such as syndrome extraction circuits).
