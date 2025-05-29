```
twobody_init(orb₀::KeplerianElements; kwargs...) -> TwoBodyPropagator
```

平均ケプラー要素 `orb₀` を使用して二体伝播器構造を作成し、初期化します。

!!! note
    伝播に使用される型は、重力定数 `m0` を定義するために使用されるものと同じです。


# キーワード

  * `m0::T`: 中心体の標準重力パラメータ [m³ / s²]。   (**デフォルト** = `tbc_m0`)
