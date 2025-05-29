```
FreeModalTimeProblem(K, M, ξn, n = size(K, 1); ismodal = false)
```

モーダル時間ソルバーのためのデータを含む構造体

**フィールド**

  * `K::VecOrMat{Real}`:

      * `ismodal = false` の場合: 剛性行列
      * `ismodal = true` の場合: 自然角周波数のベクトル
  * `M::AbtractMatrix`:

      * `ismodal = false` の場合: 質量行列
      * `ismodal = true` の場合: 質量正規化されたモード形状
  * `ξn`: 減衰比
  * `u0::Tuple`: 初期条件

      * `u0[1]`: 初期変位（またはモーダル変位）
      * `u0[2]`: 初期速度（またはモーダル速度）
  * `t::AbstractRange`: 応答を評価する時間点
  * `F::Matrix{Real}`: 外力行列（またはモーダル外力行列）
  * `n::Int`: モーダル基底に保持するモードの数
  * `ismodal::Bool`: 問題がモーダルデータを含むかどうかを示すフラグ
