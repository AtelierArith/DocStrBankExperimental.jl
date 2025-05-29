```
post!(f, r; kwargs...)
```

デフォルトの [`ExportFormat`](@ref) で結果 `r` をエクスポートします。

デフォルト形式は [`getexportformat`](@ref) を介して取得でき、[`setexportformat!`](@ref) を介して変更できます。受け入れ可能なキーワード引数は、形式と `r` のタイプによって異なります。
