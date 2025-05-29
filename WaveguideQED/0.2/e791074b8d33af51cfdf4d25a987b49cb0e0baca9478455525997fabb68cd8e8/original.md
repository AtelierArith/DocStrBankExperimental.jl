```
tensor(a::AbstractOperator,b::CavityWaveguideAbsorption)
tensor(a::CavityWaveguideAbsorption,b::AbstractOperator)
tensor(a::AbstractOperator,b::CavityWaveguideEmission)
tensor(a::CavityWaveguideEmission,b::AbstractOperator)
```

Methods for tensorproducts between QuantumOptics.jl operators and [`CavityWaveguideOperator`](@ref).
