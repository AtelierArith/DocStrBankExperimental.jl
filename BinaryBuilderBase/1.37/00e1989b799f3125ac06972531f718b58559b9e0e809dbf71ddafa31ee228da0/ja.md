```
choose_shards(p::AbstractPlatform; rootfs_build, ps_build, GCC_builds,
                           LLVM_builds, archive_type)
```

このメソッドは、`Platform`を考慮して、どのシャードをダウンロード、抽出、マウントするかを選択し、`CompilerShard`オブジェクトのリストを返します。 現在のところ、これは常に4つのシャードで構成されていますが、必ずしもそうであるとは限りません。
