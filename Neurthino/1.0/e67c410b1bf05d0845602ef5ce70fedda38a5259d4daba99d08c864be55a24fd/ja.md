```julia
MatterOscillationMatrices(
    osc_vacuum,
    energy,
    density;
    zoa,
    anti
)

```

物質を通るニュートリノの伝播のための修正された振動パラメータを作成します

# 引数

  * `osc_vacuum::OscillationParameters`: 真空中の振動パラメータ
  * `energy`: ニュートリノエネルギー [GeV]
  * `density`: 物質密度 g*cm^-3
  * `zoa`: 陽子核子比 (Z/A)
  * `anti`: 反ニュートリノであるかどうか
