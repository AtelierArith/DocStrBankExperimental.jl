```
HasReverseMode <: ReverseModeCapability
```

このトレイトは、`RuleConfig{>:HasReverseMode}` が逆モードADを実行できることを示します。これが設定されている場合、[`rrule_via_ad`](@ref) を実装する必要があります。
