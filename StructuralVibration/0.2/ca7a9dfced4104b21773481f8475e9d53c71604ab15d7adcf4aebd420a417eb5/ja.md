```
impulse_response(K::Matrix{Float64}, M::Matrix{Float64}, ξn, t, n = size(K, 1); ismat = false)
```

モーダルアプローチを使用して多自由度（Mdof）システムのインパルス応答を計算します。

**入力**

  * `K`:

      * `ismodal = false` の場合: 剛性行列
      * `ismodal = true` の場合: 自然角周波数の二乗
  * `M`:

      * `ismodal = false` の場合: 質量行列
      * `ismodal = true` の場合: 質量正規化されたモード形状
  * `ξn`: 減衰比
  * `t`: 応答を評価する時間点
  * `n`: モーダル基底に保持するモードの数
  * `ismodal::Bool`: 問題がモーダルデータを含むかどうかを示すフラグ
  * `ismat::Bool`: 出力が行列であるべきかどうかを示すフラグ

**出力**

  * `sol`: ModalImpulseSolution

      * `u`: インパルス応答行列
