```
j4(Δt::Number, orb₀::KeplerianElements; kwargs...) -> SVector{3, T}, SVector{3, T}, J4Propagator
```

入力要素 `orb₀` を使用して J4 推進器構造を初期化し、時間 Δt [s] まで軌道を伝播します。

!!! note
    伝播に使用される型は、構造 `j4c` で定義された定数を定義するために使用されたものと同じです。


# キーワード

  * `j4c::J4PropagatorConstants`: J4 軌道推進器定数 (詳細は [`J4PropagatorConstants`](@ref) を参照)。   (**デフォルト** = `j4c_egm2008`)

# 戻り値

  * `SVector{3, T}`: 伝播瞬間における慣性系で表された位置ベクトル [m]。
  * `SVector{3, T}`: 伝播瞬間における慣性系で表された速度ベクトル [m / s]。
  * [`J4Propagator`](@ref): 初期化されたパラメータを持つ構造。

# 備考

出力が表される慣性系は、軌道パラメータを生成するために使用された系に依存します。摂動理論は真の赤道を持つ慣性系を必要とすることに注意してください。
