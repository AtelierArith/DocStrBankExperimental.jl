```
setup(MC::PlutoConfig)
```

  * `default_ClimateModelSetup`を呼び出す
  * `unroll`を呼び出す
  * `notebook_launch`をタスクに追加する

```
MC1=PlutoConfig(model="examples/defaults.jl")
setup(MC1)
build(MC1)
launch(MC1)
```
