```
choose_shards(p::AbstractPlatform; rootfs_build, ps_build, GCC_builds,
                           LLVM_builds, archive_type)
```

This method chooses, given a `Platform`, which shards to download, extract and mount, returning a list of `CompilerShard` objects.  At the moment, this always consists of four shards, but that may not always be the case.
