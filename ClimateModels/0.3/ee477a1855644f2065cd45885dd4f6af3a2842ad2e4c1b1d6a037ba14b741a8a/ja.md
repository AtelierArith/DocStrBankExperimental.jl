```
build(x)
```

デフォルトは `default_ClimateModelBuild(x)` です。ほとんどの具体的な `AbstractModelConfig` の型に対して特化されることが期待されます。

```jldoctest; output = false
using ClimateModels
tmp=ModelConfig(model=ClimateModels.RandomWalker)
setup(tmp)
build(tmp)

isa(tmp,AbstractModelConfig) # hide

# output

true
```
