```
shannon!(abt::AbstractAbundanceTable; overwrite=false)
```

`abt`の各サンプルのメタデータにそのサンプルのシャノンアルファ多様性を持つ`:shannon`エントリを追加します（[`shannon`](@ref)を参照）。`overwrite=false`（デフォルト）である場合、`insert!`を使用してこの操作を実行するため、すでに`:shannon`エントリを含むサンプルがある場合はエラーが発生します。それ以外の場合は、`set!`を使用します。
