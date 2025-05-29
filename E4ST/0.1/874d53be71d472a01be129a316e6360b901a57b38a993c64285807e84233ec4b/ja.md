```
e4st_post(post_config)
```

`post_config`に対して後処理を実行します。`post_config`に関する情報は[`read_post_config`](@ref)を参照してください。後処理の一般的な概要は次のとおりです。

  * `post_data =` [`extract_results(post_config)`](@ref): `post_data`ファイルを作成し、各モジュールからの各シミュレーションの結果をそこに抽出します。
  * [`combine_results(post_config, post_data)`](@ref): モジュールが単一の結果、プロットなどに何かを結合できるようにします。出力は[`get_out_path(post_config)`](@ref)に保存します。
