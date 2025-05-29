```
Richardson <: SumHelper
```

## 説明

リチャードソン法のヘルパー。この構造体は、整数の範囲 `dom` と内部で使用される指数のリスト `exponents` で初期化されます。より多くの指数は、ノイズのコストでより良い収束をもたらす可能性があります。内部重みのフィッティングには、2つのメソッドが利用可能です： `:bender` 、 `:rohringer` 。導出については、C. Bender, A. Orszag 99, p. 375; G. Rohringer, A. Toschi 2016 を参照してください。異なるフィットメソッドのため、 `method=:bender` は使用しません。

## 使用法

## フィールド

  * **`indices`**    : フィッティングされた部分和配列のインデックスの `AbstractVector{Int}`
  * **`weights`**    : フィット重みの `Matrix{Float64}`
