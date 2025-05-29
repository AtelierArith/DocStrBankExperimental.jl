```
propagate_root(dynamics::D, jd0::V, tspan::T, q0::Vector{U}, params::NEOParameters{T};
    kwargs...) where {T <: Real, U <: Number, V <: Number D}
```

軌道をテイラー法で統合し、`NEOs.rvelea`のゼロを見つけます。

## 引数

  * `dynamics::D`: 動的モデル関数。
  * `jd0::V`: 初期ユリウス日 (TDB)。
  * `tspan::T`: 統合の時間範囲 [年単位]。
  * `q0::Vector{U}`: 初期条件のベクトル。
  * `params::NEOParameters{T}`: [`NEOParameters`](@ref)を参照。

## キーワード引数

  * `eventorder::Int`: 計算される根の`rvelea`の導関数の順序。
  * `newtoniter::Int`: 検出された根ごとの最大ニュートン-ラフソン反復回数。
  * `nrabstol::T`: ニュートン-ラフソンプロセスの許容誤差。
