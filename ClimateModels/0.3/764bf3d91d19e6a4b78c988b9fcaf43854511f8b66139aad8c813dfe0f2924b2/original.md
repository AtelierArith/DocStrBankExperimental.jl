```
compile(x)
```

Defaults to `default_ClimateModelBuild(x)`. Can be expected to be  specialized for most concrete types of `AbstractModelConfig`

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
