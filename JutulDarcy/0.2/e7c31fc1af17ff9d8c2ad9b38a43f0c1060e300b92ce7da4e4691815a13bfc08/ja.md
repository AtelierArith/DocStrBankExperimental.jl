```
simulate_data_file(inp; parse_arg = NamedTuple(), kwarg...)
```

標準入力ファイル（拡張子 .DATA）をシミュレートします。`inp` は、GeoEnergyIO 関数 `parse_data_file` の出力であるか、.DATA 拡張子を持つ入力ファイルのパスの `String` であることができます。

追加の引数は [`simulate_reservoir`](@ref) に渡されます。パーサーへの追加入力は、`setup_arg` `NamedTuple` として送信できます。
