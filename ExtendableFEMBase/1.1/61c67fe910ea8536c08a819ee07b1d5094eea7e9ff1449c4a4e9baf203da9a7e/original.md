```
function nodevalues_view(
	source::FEVectorBlock,
	operator::Type{<:AbstractFunctionOperator} = Identity)
```

Returns a vector of views of the nodal values of the source block (currently works for unbroken H1-conforming elements) that directly accesses the coefficients.
