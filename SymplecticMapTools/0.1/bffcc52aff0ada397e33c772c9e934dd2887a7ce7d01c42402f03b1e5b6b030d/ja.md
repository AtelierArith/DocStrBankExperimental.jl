```
FourierCircle <: InvariantCircle
```

コンストラクタ:

  * `FourierCircle(Na::Integer; a::AbstractArray=[], τ::Number=0., p::Integer=1)`

Fourier不変円データ構造（InvariantCircleを参照）、周期pのマップFᵖ(z)に対して不変な円zを計算するために使用されます。これは、0<=i<pのすべての円Fⁱ(z)を保存することによって行われます。円はFourier級数として保存されます。すなわち、 z(θ) = a₀ + ∑₁ᴺᵃ Aⱼ [cos(jθ), sin(jθ)]ᵀ 不変円の係数には、配列インデックスを介してチャンクでアクセスおよび設定できます。つまり、   i番目の円のa₀を取得および設定するには`z[0, i]`を使用します。   i番目の円のAⱼを取得および設定するには`z[j, i]`を使用します。
