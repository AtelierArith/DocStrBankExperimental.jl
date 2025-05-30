```
rrule_via_ad(::RuleConfig{>:HasReverseMode}, f, args...; kwargs...)
```

この関数は [`rrule`](@ref) と同じ API を持っていますが、逆モード自動微分を実行することによって動作します。 [`HasReverseMode`](@ref) 特殊機能をサポートする任意の `RuleConfig` サブタイプは、それの実装を提供しなければなりません。

関連情報: [`frule_via_ad`](@ref)、[`RuleConfig`](@ref)、および [ルール構成と AD へのコールバックに関するドキュメント](@ref config)
