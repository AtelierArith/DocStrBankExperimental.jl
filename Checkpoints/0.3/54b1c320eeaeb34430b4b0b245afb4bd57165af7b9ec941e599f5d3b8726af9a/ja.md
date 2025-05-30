```
IndexEntry(checkpoint_path, base_dir)
IndexEntry(checkpoint_path, checkpoint_name, prefixes, tags)
```

これはチェックポイントからの出力ファイルを説明するインデックスエントリです。このような出力が満載のフォルダーから、[`index_checkpoint_files`](@ref)を使用してこれらのリストを取得できます。これが`IndexEntry`が作成される通常の方法です。

内部的には、すべての`checkpoint_path`、`checkpoint_name`、`prefixes`、および`tags`を指定して直接構築されます。または（より一般的には）、そのパスが相対的である`checkpoint_path`と`base_dir`を渡すことによって構築されます。その後、すべての`checkpoint_name`、`prefixes`、および`tags`はパスから抽出できます。

IndexEntryの詳細にアクセスするために、次のヘルパーが提供されています: [`checkpoint_path`](@ref)、[`checkpoint_name`](@ref)、[`prefixes`](@ref)、[`tags`](@ref)。さらに、`getproperty`がオーバーロードされているため、`x.foo`を介してタグ`:foo`の値にアクセスできます。
