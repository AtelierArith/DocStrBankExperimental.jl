```
save(filename::AbstractString, x)
```

オブジェクト `x` を `filename` に JLD2 ファイルとして保存します。

注意: MPI モードで `save` するには、[`psave`](@ref) を使用してください。
