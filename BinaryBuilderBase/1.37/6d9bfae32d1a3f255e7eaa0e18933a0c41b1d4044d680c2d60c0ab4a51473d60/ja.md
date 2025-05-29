```
get_concrete_platform(platform::AbstractPlatform;
                      preferred_gcc_version = nothing,
                      preferred_llvm_version = nothing,
                      compilers = nothing)
```

与えられた `platform` に基づいて、GCC コンパイラ ABI に基づく具体的なプラットフォームを返します。 シャードのセットはキーワード引数によって選択されます（[`choose_shards`](@ref)を参照）。
