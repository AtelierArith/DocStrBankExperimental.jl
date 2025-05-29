```
my_artifacts_toml!(pkg::Union{Module,Base.UUID,Nothing}; versioned = false)
```

指定された `pkg` の "Artifacts.toml" へのパスを返す（または作成する）。`versioned` が true に設定されている場合、別の "Artifacts_<バージョン番号>.toml" が得られます。

参照: [`@my_artifacts_toml!`](@ref)
