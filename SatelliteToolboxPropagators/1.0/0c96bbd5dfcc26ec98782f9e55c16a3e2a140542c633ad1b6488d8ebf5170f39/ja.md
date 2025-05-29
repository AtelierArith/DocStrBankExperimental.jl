```
j2osc_init(orb₀::KeplerianElements; kwargs...) -> J2OsculatingPropagator
```

平均ケプラー要素 `orb₀` [SI単位] を使用して J2 楕円軌道伝播器構造を作成および初期化します。

!!! note
    伝播に使用される型は、構造 `j2c` で定義された定数と同じになります。


# キーワード

  * `j2c::J2PropagatorConstants`: J2 軌道伝播器定数 (詳細は [`J2PropagatorConstants`](@ref) を参照)。   (**デフォルト** = `j2c_egm2008`)
