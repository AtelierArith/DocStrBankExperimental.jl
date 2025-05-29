```
abstract type InvariantCircle
```

不変円 zᵢ の連鎖を表す抽象型であり、zᵢ₊₁ = F(zᵢ) で i<=p かつ z₀ = F(zₚ₋₁ です。このタイプの主な実装は FourierCircle ですが、他の円の潜在的な実装も存在する可能性があります。

実装は、即時の移植性のために以下の関数を持つべきです：

基本的なもの

  * 初期化子   `InvariantCircleImplementation(stuff)`
  * 同様   `Base.similar(z::InvariantCircle)`

ゲッターとセッター

  * 円ごとの未知変数の数を取得     `get_N(z::InvariantCircle)`
  * 円の周期を取得     `get_p(z::InvariantCircle)`
  * パラメータを取得（τを除く）  `get_a(z::InvariantCircle)`
  * パラメータを設定（τを除く）  `set_a!(z::InvariantCircle, a::AbstractArray)`
  * 回転数 τ を [0,2π) で取得  `get_τ(z::InvariantCircle)`
  * τ を設定  `set_τ!(z::InvariantCircle, τ::Number)`

評価関連のルーチン

  * 円を評価する（参照 `(z::InvariantCircle)(θ, i_circle)`）   `evaluate(z::InvariantCircle, θ::AbstractVector; i_circle::Integer=1)`
  * θ に関する円の導関数を評価する   `deval(z::InvariantCircle, θ::AbstractVector; i_circle::Integer=1)`
  * Nθ 等間隔点で評価された z の基底 Φ を取得する（線形性が必要）   `get_Φ(z::InvariantCircle, Nθ::Integer; τ::Number=0.0)`
  * Φ 上で不変円を評価する   `function grid_eval!(x::AbstractArray, z::InvariantCircle, Φ::AbstractArray;`                       `i_circle=0)`
  * Φ 上で不変円の導関数を評価する   `grid_deval!(dx::AbstractArray, z::InvariantCircle, Φ::AbstractArray;`               `i_circle=0)`

制約（ニュートン反復用）

  * 0 での値を制約する   `fixed_θ0_constraint(z::InvariantCircle)`

他のルーチン（継続に役立つ）

  * 平均半径を取得   `LinearAlgebra.average_radius(z::InvariantCircle)`
  * 不変円の面積を取得   `area(z::InvariantCircle; i_circle=1, Ns = 100)`
