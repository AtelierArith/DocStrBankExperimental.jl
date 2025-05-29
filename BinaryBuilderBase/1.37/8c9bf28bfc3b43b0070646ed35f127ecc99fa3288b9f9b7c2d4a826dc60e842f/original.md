```
preferred_libgfortran_version(platform::AbstractPlatform, shard::CompilerShard;
                              gcc_builds::Vector{GCCBuild} = available_gcc_builds)
```

Return the libgfortran version preferred by the given platform or GCCBootstrap shard.
