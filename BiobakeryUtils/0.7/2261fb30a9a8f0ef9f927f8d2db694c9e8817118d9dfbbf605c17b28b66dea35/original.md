```
humann_barplot(comm::CommunityProfile, outpath; kwargs...)
```

Wrapper for `humann_barplot` script, to generate plots from functional data. pass keyword arguments for script options. Flag arguments should be set to `true`. eg

```julia-repl
julia> humann_barplot(comm, "plot.png"; focal_metadata="STSite", focal_feature="COA-PWY",
                      sort="braycurtis",
                      scaling="logstack",
                      as_genera=true,
                      remove_zeros=true)
```

Requires installation of [`humann`](https://github.com/biobakery/humann) available in `ENV["PATH"]`. See "[Using Conda](@ref using-conda)" for more information.
