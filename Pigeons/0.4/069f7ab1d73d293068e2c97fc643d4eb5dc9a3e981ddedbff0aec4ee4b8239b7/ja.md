```julia
PT(inputs; exec_folder)

```

提供された [`Inputs`](@ref) から PT 構造体を作成します。オプションで、特定の `exec_folder` パス (`AbstractString`) を提供できます。提供しない場合は、[`next_exec_folder()`](@ref) を介して作成されます。
