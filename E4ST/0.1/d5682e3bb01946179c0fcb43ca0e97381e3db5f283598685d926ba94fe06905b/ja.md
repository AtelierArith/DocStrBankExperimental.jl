```
read_data(config) -> data
```

`config`にリストされたファイルからデータを読み込み、`data`に格納します。

以下の関数を呼び出します：

  * [`read_data_files!(config, data)`](@ref) - ファイルからデータを読み込みます
  * [`modify_raw_data!(config, data)`](@ref) - データがセットアップされる前に、[`Modification`](@ref)が生データを修正する機会を与えます。
  * [`setup_data!(config, data)`](@ref) - 必要に応じてデータをセットアップし、テーブルを修正/追加します。
  * [`modify_setup_data!(config, data)`](@ref) - モデルが構築される前に、[`Modification`](@ref)がセットアップデータを修正する機会を与えます。
