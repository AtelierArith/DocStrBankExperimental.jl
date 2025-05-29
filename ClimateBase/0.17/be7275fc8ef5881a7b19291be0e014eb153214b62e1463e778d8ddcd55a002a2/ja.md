```
ncwrite(file::String, Xs; globalattr = Dict())
```

与えられた `ClimArray` インスタンス（`ClimArray` の iterable または単一の `ClimArray`）を、NCDatasets.jl を使用して CF 標準規約に従って `.nc` ファイルに書き込みます。オプションで、`.nc` ファイルのグローバル属性を指定できます。

`Xs` 内の配列のメタデータや次元は、`.nc` ファイルに適切に書き込まれ、必要な型変換は自動的に行われます。

**警告**: `Xs` の間で共有される次元は同一であると仮定します。

[`ncread`](@ref) も参照してください。
