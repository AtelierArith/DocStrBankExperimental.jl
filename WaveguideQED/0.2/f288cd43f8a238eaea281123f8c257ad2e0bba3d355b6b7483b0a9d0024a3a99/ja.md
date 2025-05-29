```
get_waveguide_operators(basis::LazySum)
get_waveguide_operators(basis::LazyProduct)
get_waveguide_operators(basis::LazyTensor)
get_waveguide_operators(basis::Tuple)
get_waveguide_operators(basis::Array)
get_waveguide_operators(basis::WaveguideOperator)
```

すべての[`WaveguideOperator`](@ref)をLazyOperator内またはオペレーターのリストから返します。[`WaveguideOperator`](@ref)が見つからない場合は、空の配列が返されます。
