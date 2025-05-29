```
ModalFRFProblem(ωn, ξn, freq, ϕo, ϕe)
```

モーダルソルバーにFRFを計算するためのデータを供給する構造体

**フィールド**

  * `ωn::Vector{Real}`: 自然角周波数
  * `ξn::Vector{Real}`: モーダル減衰比
  * `freq::AbstractRange`: 興味のある周波数
  * `ϕe::AbstractMatrix`: 励起点でのモード形状
  * `ϕo::AbstractMatrix`: 観測点でのモード形状

**注意** モード形状は質量正規化されている必要があります
