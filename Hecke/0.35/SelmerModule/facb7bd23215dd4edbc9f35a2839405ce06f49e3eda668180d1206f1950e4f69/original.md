```
pselmer_group(p::Int, S::Vector{AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}}; check::Bool = true, algo::Symbol = :raw)
```

Similar to the `pselmer_group_fac_elem`, the difference is that the elements here are evaluated, ie. returned explicitly wrt the basis of the number field.
