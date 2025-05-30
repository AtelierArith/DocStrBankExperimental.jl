```
frule_via_ad(::RuleConfig{>:HasForwardsMode}, ȧrgs, f, args...; kwargs...)
```

この関数は [`frule`](@ref) と同じ API を持っていますが、順方向モードの自動微分を実行することによって動作します。 [`HasForwardsMode`](@ref) 特殊機能をサポートする任意の `RuleConfig` サブタイプは、それの実装を提供する必要があります。

関連情報: [`rrule_via_ad`](@ref)、[`RuleConfig`](@ref)、および [ルール構成と AD へのコールバックに関するドキュメント](@ref config)
