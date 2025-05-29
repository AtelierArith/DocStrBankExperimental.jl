```
combine_results(post_mod::Modification, post_config, post_mod_data)
```

Combine results and probably save them to the out path specified in `post_config`.

`post_mod_data` is the porton of `post_data` for this particular `post_mod`, an OrderedDict mapping `sim_name` to the extracted `results` from [`extract_results`](@ref).
