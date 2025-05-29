```
params, signal = load_nxs(filename; field="signal")
```

Mantidからエクスポートされた`MDHistoWorkspace`ファイルの名前を指定して、そのファイルから[`BinningParameters`](@ref)と信号をロードします。

信号の代わりに別のフィールドをロードするには、例えば`field="errors_squared"`と指定します。一般的なフィールドには`errors_squared`、`mask`、`num_events`、および`signal`が含まれます。
