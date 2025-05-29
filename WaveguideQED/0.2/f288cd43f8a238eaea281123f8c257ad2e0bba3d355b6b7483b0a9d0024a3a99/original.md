```
get_waveguide_operators(basis::LazySum)
get_waveguide_operators(basis::LazyProduct)
get_waveguide_operators(basis::LazyTensor)
get_waveguide_operators(basis::Tuple)
get_waveguide_operators(basis::Array)
get_waveguide_operators(basis::WaveguideOperator)
```

Returns all [`WaveguideOperator`](@ref) in LazyOperator or from a list of operators. If no [`WaveguideOperator`](@ref) is found, and empty array is returned.
