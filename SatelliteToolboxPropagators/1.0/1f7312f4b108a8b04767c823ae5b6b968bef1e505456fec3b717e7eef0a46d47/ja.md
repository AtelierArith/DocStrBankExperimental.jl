```
j4_init(orb₀::KeplerianElements; kwargs...) -> J4Propagator
```

平均ケプラー要素 `orb₀` を使用して J4 軌道伝播器構造を作成および初期化します。

!!! note
    伝播に使用される型は、構造 `j4c` で定義された定数と同じになります。


# キーワード

  * `j4c::J4PropagatorConstants`: J4 軌道伝播器定数 (詳細は [`J4PropagatorConstants`](@ref) を参照)。 (**デフォルト** = `j4c_egm2008`)
