```
compile(x)
```

デフォルトは `default_ClimateModelBuild(x)` です。ほとんどの具体的な `AbstractModelConfig` の型に対して特化されることが期待されます。

```jldoctest; output = false
using ClimateModels, Pkg
tmp0=PackageSpec(url="https://github.com/JuliaOcean/AirSeaFluxes.jl")
tmp=ModelConfig(model=tmp0)
setup(tmp)
compile(tmp)

isa(tmp,AbstractModelConfig)

# output

true
```
