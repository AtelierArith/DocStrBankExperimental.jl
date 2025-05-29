```
analyze_manifest([path_to_manifest]; registries=reachable_registries(),
                 auth=github_auth(), sleep=0)
```

[`find_packages_in_manifest`](@ref) を実行し、その結果に対して [`analyze`](@ref) を実行するための便利な関数です。位置引数 `path_to_manifest` のデフォルトは `joinpath(dirname(Base.active_project()), "Manifest.toml")` です。
