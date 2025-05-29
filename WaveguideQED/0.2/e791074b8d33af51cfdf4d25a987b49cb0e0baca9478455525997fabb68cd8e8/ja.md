```
tensor(a::AbstractOperator,b::CavityWaveguideAbsorption)
tensor(a::CavityWaveguideAbsorption,b::AbstractOperator)
tensor(a::AbstractOperator,b::CavityWaveguideEmission)
tensor(a::CavityWaveguideEmission,b::AbstractOperator)
```

QuantumOptics.jl オペレーターと [`CavityWaveguideOperator`](@ref) の間のテンソル積のためのメソッド。
