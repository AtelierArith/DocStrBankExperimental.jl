```
extract_results(post_config) -> post_data::OrderedDict{Symbol, Any}
```

`post_data`を初期化し、`post_config[:mods]`の各修正に対して、`post_config[:sim_paths]`および`post_config[:sim_names]`の各シミュレーションの結果を抽出します。

`extract_results(post_mod, config, data)`を各`post_mod`に対して呼び出します。ここで、`config`はシミュレーションの設定であり、`data`は`read_processed_results`から読み込まれたシミュレーションデータです。
