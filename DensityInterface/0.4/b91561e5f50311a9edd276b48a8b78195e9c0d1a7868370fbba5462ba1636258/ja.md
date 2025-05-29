```
logdensityof(object)
```

与えられた点での密度 `object`（またはその関連する密度）の対数値を計算する関数を返します。

```jldoctest a
julia> log_f = logdensityof(object); log_f isa Function
true

julia> log_f(x) == logdensityof(object, x)
true
```

`logdensityof(object)` は `Base.Fix1(logdensityof, object)` にデフォルト設定されていますが、特化される場合があります。その場合、[`logfuncdensity`](@ref) は通常、`logdensityof` の戻り値の型に特化される必要があります。

[`logfuncdensity`](@ref) は `logdensityof` の逆であるため、`logfuncdensity(log_f)` は `object` と同等でなければなりません。
