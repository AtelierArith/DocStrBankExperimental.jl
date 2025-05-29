```
setup(MC::PlutoConfig)
```

  * call `default_ClimateModelSetup`
  * call `unroll`
  * add `notebook_launch` to tasks

```
MC1=PlutoConfig(model="examples/defaults.jl")
setup(MC1)
build(MC1)
launch(MC1)
```
