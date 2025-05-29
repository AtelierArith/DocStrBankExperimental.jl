```
preferred_cxxstring_abi(platform::AbstractPlatform, shard::CompilerShard;
                        gcc_builds::Vector{GCCBuild} = available_gcc_builds)
```

Return the C++ string ABI preferred by the given platform or GCCBootstrap shard.
