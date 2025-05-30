```
RuleConfig{T}
```

使用するルールの設定。 `T`: **トレイト**。これは、あなたのADに対してルールが定義されることを許可するために必要なすべての特別なトレイトの `Union` であるべきです。特別なものがない場合、これは `Union{}` に設定されるべきです。

**ADの著者**は、`frule`/`rrule` を呼び出す際に使用するために `RuleConfig` のサブタイプを定義するべきです。

**ルールの著者**は、ルールを定義する際にこの設定に基づいてディスパッチすることができます。例えば：

```julia
# 変異がサポートされているADシステムでのみ `pop!` のためのrruleを定義します。
rrule(::RuleConfig{>:SupportsMutation}, typeof(pop!), ::Vector) = ...

# このmapの定義は、フォワードモードを定義する任意のADのためのものです。
rrule(conf::RuleConfig{>:HasForwardsMode}, typeof(map), ::Vector) = ...

# このmapの定義は、リバースモードのみを定義する任意のADのためのものです。
# これは、ADがフォワードモードも定義している場合に使用できるrruleほど良くはありません。
rrule(conf::RuleConfig{>:Union{NoForwardsMode, HasReverseMode}}, typeof(map), ::Vector) = ...
```

詳細については、[ルール設定とADへのコールバック](@ref config)を参照してください。
