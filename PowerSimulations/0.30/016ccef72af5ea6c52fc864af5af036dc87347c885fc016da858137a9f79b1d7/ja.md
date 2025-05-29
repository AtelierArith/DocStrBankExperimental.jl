```julia
template_unit_commitment(
;
    kwargs...
) -> PowerSimulations.ProblemTemplate

```

```
template_unit_commitment(; kwargs...)
```

ユニットコミットメント問題のデフォルトのDeviceModelsを持つ`ProblemTemplate`を作成します。

# 例

template = template*unit*commitment()

```

# 受け入れられるキーワード
- `network::Type{<:PM.AbstractPowerModel}` : デフォルトのネットワークモデル設定を上書きします
- `devices::Vector{DeviceModel}` : デフォルトの`DeviceModel`設定を上書きします
- `services::Vector{ServiceModel}` : デフォルトの`ServiceModel`設定を上書きします
```
