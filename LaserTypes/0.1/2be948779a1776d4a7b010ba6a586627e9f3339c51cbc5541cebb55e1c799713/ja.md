```
struct LaguerreGaussLaser <: AbstractLaser
```

`LaguerreGaussLaser`は、レーザーの`units`（位置引数で、`:SI`、`:atomic`、`:SI_unitful`、`:atomic_unitful`のいずれか）と以下のパラメータによって定義されます。

  * `λ`はレーザーの波長です。
  * `a₀`は正規化されたベクトルポテンシャルで、$a_0=\frac{eA}{m_e c^2}$として定義されます。
  * `ϕ₀`は初期位相で、デフォルト値は0.0です。
  * `w₀`はレイリー範囲でのビーム半径または[ビームウエスト](https://en.wikipedia.org/wiki/Gaussian_beam#Beam_waist)です。
  * `ξx`と`ξy`は偏光を示し、デフォルト値は`1.0 + 0im`と`0.0 + 0im`です。
  * `orientation`はレーザーがデフォルトの座標系に対してどのように向いているかを指定します（デフォルトは`(:x, :z)`）。詳細については[`LaserGeometry`](@ref)を参照してください。
  * `propagation_dir`は、内因的座標系における波の伝播方向を示します（デフォルトは`:z`）。詳細については[`LaserGeometry`](@ref)を参照してください。
  * `profile`はパルスの時間プロファイルで、デフォルトは一定（無限のパルス持続時間）です。
  * `p`はモードの半径インデックスで、$p ∈ ℤ, p ≥ 0$、デフォルト値は1です。
  * `m`はモードの方位インデックスで、$m ∈ ℤ$、デフォルト値は0です。

`LaguerreGaussLaser`型の初期化中に、いくつかの有用な導出値も計算されます。

  * `ω`は角周波数で、$2π c / λ$で与えられます。
  * `k`は波数で、$2π / λ$で与えられます。
  * `z_R`は[レイリー範囲](https://en.wikipedia.org/wiki/Rayleigh_length)で、$k w_0^2 / 2$で与えられます。
  * `T₀`はレーザーの周期で、$2π / ω$で与えられます。
  * `E₀`は電場の振幅で、$a_0\frac{m_q c \omega}{q}$で与えられます。
  * `Nₚₘ`は正規化因子で、$\sqrt{(p+1)_{|m|}}$で与えられ、$(x)_n$は[ポッハンマー記号](https://mathworld.wolfram.com/PochhammerSymbol.html)です。
