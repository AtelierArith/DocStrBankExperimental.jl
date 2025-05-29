```
humann_rename(comm::AbstractDataFrame; kind::String="ec")
```

Wrapper for `humann_rename_table` script, returning a CommunityProfile with re-named features.

Requires installation of [`humann`](https://github.com/biobakery/humann) available in `ENV["PATH"]`. See "[Using Conda](@ref using-conda)" for more information.
