```
twobody_init!(tbd::TwoBodyPropagator, orb₀::KeplerianElements; kwargs...) -> Nothing
```

二体伝播器構造 `tbd` を平均ケプラー要素 `orb₀` を使用して初期化します。

!!! warning
    `tbd` の伝播定数 `μ::Number` は変更されません。したがって、初期化する必要があります。

