```
combine_results(post_mod::Modification, post_config, post_mod_data)
```

結果を結合し、`post_config`で指定された出力パスに保存する可能性があります。

`post_mod_data`は、この特定の`post_mod`のための`post_data`のポートンであり、`sim_name`を[`extract_results`](@ref)から抽出された`results`にマッピングするOrderedDictです。
