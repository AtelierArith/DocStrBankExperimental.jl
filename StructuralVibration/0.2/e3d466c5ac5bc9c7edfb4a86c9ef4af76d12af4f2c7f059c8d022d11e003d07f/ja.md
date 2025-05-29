```
ModalFreqProblem(ωn, ξn, Fn, freq, ϕo)
```

モーダルアプローチによる周波数応答を計算するためのモーダルソルバーにデータを供給する構造体

**フィールド**

  * `ωn::Vector{Real}`: 自然角周波数
  * ξn::Vector{Real}: モーダル減衰比
  * `Ln::AbstractMatrix`: モーダル参加係数
  * `freq::AbstractRange`: 興味のある周波数
  * `ϕo::Matrix{Real}`: 観測点でのモード形状

```
