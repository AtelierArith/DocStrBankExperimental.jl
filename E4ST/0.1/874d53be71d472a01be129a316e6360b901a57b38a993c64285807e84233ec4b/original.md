```
e4st_post(post_config)
```

Runs post-processing on `post_config`.  See [`read_post_config`](@ref) for information about the `post_config`.  The general outline of post processing is:

  * `post_data =` [`extract_results(post_config)`](@ref): Create a `post_data` file and extract the results from each simulation from each mod into it.
  * [`combine_results(post_config, post_data)`](@ref): allow the mod to combine anything into a single result, plot, etc.  Store any output into [`get_out_path(post_config)`](@ref).
