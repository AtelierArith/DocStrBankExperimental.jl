```
apply_remap(outfile::AbstractString, infile::AbstractString, weightfile::AbstractString, vars; verbose=false)
```

NetCDFファイル `infile` を `outfile` にリマップし、[`remap_weights`](@ref) を介して構築されたリマッピングウェイト `weightfile` を使用します。 `vars` はリマップする変数名のコレクションである必要があります。

情報を印刷するには `verbose=true` に設定します。

[Tempest remap: オフラインマップアプリケーション](https://github.com/ClimateGlobalChange/tempestremap/#offline-map-application) を参照してください。
