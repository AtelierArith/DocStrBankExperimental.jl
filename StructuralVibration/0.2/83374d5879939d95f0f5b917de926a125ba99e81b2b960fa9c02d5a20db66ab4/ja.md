```
DirectTimeProblem(K, M, C, F, u0, t)
```

時間ソルバーのためのデータを含む構造体

**コンストラクタ**

  * `K::AbstractMatrix`: 剛性行列
  * `M::AbstractMatrix`: 質量行列
  * `C:AbstractMatrix`: 減衰行列
  * `F::AbstractMatrix`: 外力行列
  * `u0::Tuple`: 初期条件

      * `u0[1]`: 初期変位（またはモーダル変位）
      * `u0[2]`: 初期速度（またはモーダル速度）
  * `t::AbstractVector`: 応答を評価する時間点

**フィールド**

  * `K`: 剛性行列
  * `M`: 質量行列
  * `C`: 減衰行列
  * `F`: 外力行列
  * `u0`: 初期条件

      * `u0[1]`: 初期変位
      * `u0[2]`: 初期速度
  * `h::Real`: タイムステップ
