```
JuMP.constraint_ref_with_index(
element::OptiElement, 
idx::MOI.ConstraintIndex{<:MOI.AbstractScalarFunction, <:MOI.AbstractScalarSet}
)
```

Return a `ConstraintRef` given an optigraph element and `MOI.ConstraintIndex`.  Note that the index is the index corresponding to the graph backend, not the element index.
