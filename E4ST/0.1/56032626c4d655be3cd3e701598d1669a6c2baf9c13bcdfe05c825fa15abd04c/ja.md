```
summarize_post_config() -> summary
```

`post_config`を要約し、以下の列を含みます：

  * `name` - プロパティ名、すなわちキー
  * `required` - プロパティが必須かどうか
  * `default` - このプロパティのデフォルト値
  * `description`

| name            | required | default                                                     | description                                                                                              |
|:--------------- |:-------- |:----------------------------------------------------------- |:-------------------------------------------------------------------------------------------------------- |
| `sim_paths`     | true     | nothing                                                     | 希望するシミュレーション出力へのパス。                                                                                      |
| `sim_names`     | false    | nothing                                                     | 各シミュレーションの名前。これは後処理で使用されます。指定がない場合、`e4st_post`は各`sim_paths`の設定を確認して`name`が指定されているかどうかを確認します。             |
| `base_sim_name` | false    |                                                             | 比較に使用するベースシミュレーションの名前。修正によって使用されます。                                                                      |
| `out_path`      | true     | nothing                                                     | 後処理の結果のための希望する出力パスへのパス。                                                                                  |
| `mods`          | false    | OrderedCollections.OrderedDict{Symbol, E4ST.Modification}() | `e4st_post`の実行方法を指定する`Modification`のリスト。 [`extract_results`](@ref)および[`combine_results`](@ref)を参照してください。 |
