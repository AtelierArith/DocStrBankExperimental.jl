```
ginisimpson!(abt::AbstractAbundanceTable; overwrite=false)
```

各サンプルのメタデータにそのサンプルのジニ・シンプソンα多様性を持つ`:ginisimpson`エントリを`abt`に追加します（[`ginisimpson`](@ref)を参照）。`overwrite=false`（デフォルト）である場合、`insert!`を使用してこの操作を実行するため、すでに`:ginisimpson`エントリを含むサンプルがある場合はエラーが発生します。それ以外の場合は、`set!`を使用します。
