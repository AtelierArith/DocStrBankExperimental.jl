```
num_coeff(a::FunctionFieldElem, n::Int)
```

Return the degree `n` coefficient of the numerator of the element `a` (in its polynomial representation in terms of the generator of the function field, rationalised as per `numerator/denominator` described above). The coefficient will be an polynomial over the `base_ring` of the underlying rational function field.
