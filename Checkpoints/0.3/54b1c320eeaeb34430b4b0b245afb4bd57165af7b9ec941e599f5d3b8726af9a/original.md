```
IndexEntry(checkpoint_path, base_dir)
IndexEntry(checkpoint_path, checkpoint_name, prefixes, tags)
```

This is an index entry describing the output file from a checkpoint. You can retrieve a list of these from a folder full of such outputs, using [`index_checkpoint_files`](@ref), this is the normal way that `IndexEntry`'s are created.

Internally, it is constructed either directly, specifying all of the `checkpoint_path`, `checkpoint_name`, `prefixes`, and `tags`. Or (more usually) by passing in the `checkpoint_path` and the `base_dir` that that path is relative to; then all the `checkpoint_name`, `prefixes` and `tags` can be extracted from the path.

For accessing details of the IndexEntry the following helpers are provided: [`checkpoint_path`](@ref), [`checkpoint_name`](@ref), [`prefixes`](@ref), [`tags`](@ref). Further: `getproperty` is overloaded so that you can access the value of the tag `:foo` via `x.foo`.
