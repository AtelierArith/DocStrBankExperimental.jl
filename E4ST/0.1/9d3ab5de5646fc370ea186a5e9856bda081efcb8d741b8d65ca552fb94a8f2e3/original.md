```
combine_results(post_config, post_data) -> nothing
```

Combine results for each of the `mods` in `post_config[:mods]`.  Calls `combine_results(post_mod, post_config, post_mod_data)`, where `post_mod_data` is `post_data[mod_name]`.
