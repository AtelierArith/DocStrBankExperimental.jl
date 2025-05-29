```
mirror_tarball(registry, upstreams::AbstractVector, static_dir::String; kwargs...)
```

Generating all static contents for registry `registry`.

After building, all static content data are saved to `static_dir`:

  * `/registries`: map of registry uuids at this server to their current tree hashes
  * `/registry/$uuid/$hash`: tarball of registry uuid at the given tree hash
  * `/package/$uuid/$hash`: tarball of package uuid at the given tree hash
  * `/artifact/$hash`: tarball of an artifact with the given tree hash

Set environment variable `JULIA_NUM_THREADS` to enable multi-threads.

# Keyword parameters

  * `http_parameters::Dict{Symbol, Any}`: any parameters that need to pass to `HTTP.get` when fetching resources.
  * `packages::AbstractVector{Package}`: manually create and specify a set of packages that needed to be stored. This  can be used to build only a partial of the complete storage. Check [`read_packages`](@ref read_packages) for how  to build packages info.
  * `show_progress::Bool`: `true` to show an additional progress meter. By default it is `true`.
  * `skip_duration::Real`: specify for how long (hours) you want to skip the resources listed in `/failed_resources.txt`  until the next try of them. By default it is `24` hours.
