```
強制モーダル時間問題(K, M, ξn, u0, t, F, n = size(K, 1); ismodal = false)
```

任意の励起による強制応答を計算するためのモーダル時間ソルバー用のデータを含む構造体

**フィールド**

  * `K::VecOrMat{Real}`:

      * `ismodal = false` の場合 `Matrix{Real}`: 剛性行列
      * `ismodal = true` の場合 `Vector{Real}`: 自然角周波数
  * `M::AbtractMatrix`:

      * `ismodal = false`: 質量行列
      * `ismodal = true`: 質量正規化モード形状
  * `ξn`: 減衰比
  * `F::Matrix{Real}`: 外力行列（またはモーダル参加係数）
  * `u0::Tuple`: 初期条件

      * `u0[1]`: 初期変位（またはモーダル変位）
      * `u0[2]`: 初期速度（またはモーダル速度）
  * `t::AbstractRange`: 応答を評価する時間点
  * `n::Int`: モーダル基底に保持するモードの数
  * `ismodal::Bool`: 問題がモーダルデータを含むかどうかを示すフラグ
