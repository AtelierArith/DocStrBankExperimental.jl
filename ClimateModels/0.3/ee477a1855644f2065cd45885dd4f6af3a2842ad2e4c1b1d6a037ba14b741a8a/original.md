```
build(x)
```

Defaults to `default_ClimateModelBuild(x)`. Can be expected to be  specialized for most concrete types of `AbstractModelConfig`

```jldoctest; output = false
using ClimateModels
tmp=ModelConfig(model=ClimateModels.RandomWalker)
setup(tmp)
build(tmp)

isa(tmp,AbstractModelConfig) # hide

# output

true
```
