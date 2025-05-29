```
eos(model::EoSModel, V, T, z=SA[1.0])
```

全ヘルムホルツ自由エネルギーを返します。

# 入力:

  * `model::EoSModel` 評価する熱力学モデル
  * `V` 総体積、単位は [m³]
  * `T` 温度、単位は [K]
  * `z` モル量、単位は [mol]、デフォルトは `@SVector [1.0]`

# 出力:

  * 総ヘルムホルツ自由エネルギー、単位は [J]

デフォルトでは、`R̄*T*∑(z)*(a_ideal(ideal_model,V,T,z) + a_res(model,V,T,z))` を呼び出します。ここで `ideal_model == idealmodel(model)` であり、`a_res` は縮約残差ヘルムホルツエネルギー、`a_ideal` は縮約理想ヘルムホルツエネルギーです。理想モデルを混ぜ合わせることができます。提供する場合:

  * `[idealmodel](@ref)(model)`: あなたの熱力学モデルから理想モデルを抽出します
  * `[a_res](@ref)(model,V,T,z)`: 残差縮約ヘルムホルツ自由エネルギー
