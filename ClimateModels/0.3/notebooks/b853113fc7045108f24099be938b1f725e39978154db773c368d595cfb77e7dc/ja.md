```
update(MC::PlutoConfig)
```

ノートブックの依存関係を更新します（`unroll` & `reroll`を介して）および初期ノートブックファイルを置き換えます。

```
update(PlutoConfig(model="examples/defaults.jl"))
run(PlutoConfig(model="examples/defaults.jl"))
```
