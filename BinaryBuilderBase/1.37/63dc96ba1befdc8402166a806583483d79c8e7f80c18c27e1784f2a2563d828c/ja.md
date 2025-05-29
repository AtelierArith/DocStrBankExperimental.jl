```
preferred_cxxstring_abi(platform::AbstractPlatform, shard::CompilerShard;
                        gcc_builds::Vector{GCCBuild} = available_gcc_builds)
```

指定されたプラットフォームまたはGCCBootstrapシャードによって推奨されるC++文字列ABIを返します。
