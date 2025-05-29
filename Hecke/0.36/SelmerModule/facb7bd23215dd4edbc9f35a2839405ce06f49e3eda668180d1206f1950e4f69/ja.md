```
pselmer_group(p::Int, S::Vector{AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}}; check::Bool = true, algo::Symbol = :raw)
```

`pselmer_group_fac_elem`と似ていますが、ここでの要素は評価されており、すなわち数体の基底に関して明示的に返されます。
