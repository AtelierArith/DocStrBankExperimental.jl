```
put!(x :: AbstractModelConfig,v)
```

Adds `v` to x.channel (i.e. `put!(x.channel,v)`)

```jldoctest; output = false
using ClimateModels, Suppressor
tmp=ModelConfig()
setup(tmp)
put!(tmp,ClimateModels.RandomWalker)
ClimateModels.pause(tmp)
@suppress ClimateModels.monitor(tmp)
@suppress ClimateModels.help(tmp)
launch(tmp)

isa(tmp,AbstractModelConfig)

# output

true
```
