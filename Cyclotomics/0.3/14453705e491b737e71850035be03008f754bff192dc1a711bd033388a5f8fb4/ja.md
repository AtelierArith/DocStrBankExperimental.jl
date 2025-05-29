```
Cyclotomic(coeffs::AbstractVector)
```

`coeffs`として保存された係数を持つ`length(coeffs)`-次の巡回体の要素。

巡回体の内部にアクセスするには、API関数を使用します：

  * `conductor` - 巡回体の導体、すなわち現在ストレージに使用されている`n`。これは巡回体の最小埋め込み体ではない可能性があります。
  * `coeffs` - 係数を含む基礎ベクトルへの参照を返します。
  * `getindex`/`setindex!` - `α[i]`を使用して、単位根の`i`-次の冪の係数にアクセスします（循環的に）。
  * `values`/`exponents` - *非ゼロ*の係数/指数に対応する*非ゼロ*の係数に対するペアイテレータ
  * `normalform!` - 巡回体をZumbroich基底によって与えられた唯一の表現に持っていきます（変更しない形式でも利用可能）。

`Cyclotomic`内の非ゼロ係数の反復は、指数と対応する係数のペア`(exp, coeff)`を生成する`exps_coeffs`によって提供されます。
