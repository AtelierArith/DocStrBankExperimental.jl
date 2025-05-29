```julia
template_economic_dispatch(
;
    kwargs...
) -> PowerSimulations.ProblemTemplate

```

```
template_economic_dispatch(; kwargs...)
```

経済 dispatch 問題のデフォルト DeviceModels を持つ `ProblemTemplate` を作成します。

# 例

template = template*economic*dispatch()

```

# 受け入れられるキーワード
- `network::Type{<:PM.AbstractPowerModel}` : デフォルトのネットワークモデル設定を上書きします
- `devices::Vector{DeviceModel}` : デフォルトの `DeviceModel` 設定を上書きします
- `services::Vector{ServiceModel}` : デフォルトの `ServiceModel` 設定を上書きします
```
