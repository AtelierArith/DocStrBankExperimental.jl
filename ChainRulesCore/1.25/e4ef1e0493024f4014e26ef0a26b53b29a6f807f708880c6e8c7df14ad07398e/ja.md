```
HasForwardsMode <: ForwardsModeCapability
```

このトレイトは、`RuleConfig{>:HasForwardsMode}` が順方向モードのADを実行できることを示します。これが設定されている場合、[`frule_via_ad`](@ref) を実装する必要があります。
