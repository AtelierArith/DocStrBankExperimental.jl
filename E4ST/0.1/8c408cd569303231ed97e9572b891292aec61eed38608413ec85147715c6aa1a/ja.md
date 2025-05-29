```
make_out_path!(config) -> nothing
```

`config[:out_path]` が提供されている場合、何もしません。それ以外の場合は、`config[:base_out_path]` が存在することを確認し、必要に応じて作成します。新しいタイムスタンプ付きフォルダーを [`time_string`](@ref) を介して作成し、それを `config[:out_path]` に保存します。出力ファイルのパスを作成するには [`get_out_path`](@ref) を参照してください。
