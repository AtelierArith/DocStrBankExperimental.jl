```
struct LorentzianSD <: AbstractSD
```

LorentzianSDはローレンツianスペクトル密度を表します。これは、結合の強さを表す振幅`α`、ピーク中心周波数`ω0`、およびローレンツianピークの幅`Γ`によって特徴付けられます。すなわち

$$
J(\omega) = \frac{\alpha\Gamma}{\pi}\frac{\omega}{(\omega^2 - \omega_0^2)^2 + \omega^2\Gamma^2}
$$

# フィールド

  * `α::Float64`: 結合の強さを示す振幅`α`。
  * `ω0::Float64`: ローレンツianピークの中心周波数。
  * `Γ::Float64`: ローレンツianピークの幅。
