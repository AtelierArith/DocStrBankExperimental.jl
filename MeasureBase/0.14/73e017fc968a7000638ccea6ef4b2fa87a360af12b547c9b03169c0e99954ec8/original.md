```
struct PowerMeasure{M,...} <: AbstractProductMeasure
```

A power measure is a product of a measure with itself. The number of elements in the product determines the dimensionality of the resulting support.

Note that power measures are only well-defined for integer powers.

The nth power of a measure μ can be written μ^n.
