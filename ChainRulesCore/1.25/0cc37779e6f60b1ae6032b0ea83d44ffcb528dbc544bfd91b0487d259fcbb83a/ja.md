```
NoForwardsMode <: ForwardsModeCapability
```

これは[`HasForwardsMode`](@ref)の補完です。曖昧さを避けるために、フォワードモードADをサポートしない[`RuleConfig`]は`RuleConfig{>:NoForwardsMode}`であるべきです。
