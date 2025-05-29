```
load(filename::AbstractString)
```

`filename`で指定されたJLD2ファイルに保存されたオブジェクトをロードします。

注意: MPIモードで`load`するには、[`pload`](@ref)を使用してください。
