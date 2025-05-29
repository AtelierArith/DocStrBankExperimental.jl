```
StateSpaceProblem(css::ContinuousStateSpace, u0::Vector{Float64}, h::Float64, F::Matrix{Float64})
```

状態空間モデルのデータを含む構造体

**コンストラクタ**

  * `css`: 連続時間状態空間モデル
  * `u0`: 初期条件
  * `F`: 外部力行列
  * `t`: 時間ベクトル

**フィールド**

  * `css`: ContinuousStateSpace
  * `F`: 外部力行列
  * `u0`: 初期条件
  * `h`: 時間ステップ
