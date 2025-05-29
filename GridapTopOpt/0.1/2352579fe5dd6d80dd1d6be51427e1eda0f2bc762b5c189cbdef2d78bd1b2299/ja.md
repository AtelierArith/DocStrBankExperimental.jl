```
load!(filename::AbstractString, x)
```

`filename`にあるJLD2ファイルに保存されたオブジェクトをロードし、その内容を`x`にコピーします。

注意: MPIモードで`load!`を使用するには、[`pload!`](@ref)を使用してください。
