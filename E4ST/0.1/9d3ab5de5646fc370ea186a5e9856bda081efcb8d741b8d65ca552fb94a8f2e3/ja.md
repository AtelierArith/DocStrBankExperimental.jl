```
combine_results(post_config, post_data) -> nothing
```

`post_config[:mods]` の各 `mods` の結果を結合します。 `combine_results(post_mod, post_config, post_mod_data)` を呼び出し、ここで `post_mod_data` は `post_data[mod_name]` です。
