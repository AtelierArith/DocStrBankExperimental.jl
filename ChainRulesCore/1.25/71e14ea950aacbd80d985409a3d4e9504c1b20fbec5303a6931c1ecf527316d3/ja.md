```
NoReverseMode <: ReverseModeCapability
```

これは[`HasReverseMode`](@ref)の補完です。逆モードADを実行することをサポートしない[`RuleConfig`]は、曖昧さを避けるために`RuleConfig{>:NoReverseMode}`であるべきです。
