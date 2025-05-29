```
take!(x :: AbstractModelConfig)
```

Takes command `v` from x.channel (i.e. `take!(x.channel)`) and execute `v(x)`  (if a Function) or return `v` (if not a Function, e.g. a String).

```
tmp=ModelConfig()
put!(tmp,ClimateModels.RandomWalker)
take!(tmp)
```
