```
データ
```

このモジュールには、[`Possibility`](@ref) タイプのコレクションと、それらを構築するためのいくつかの便利なユーティリティ関数が含まれています。

現在含まれているものは次のとおりです：

  * [`Integers{T}`](@ref)、整数型を生成するためのもの（`BigInt`を除く）
  * [`Floats{F}`](@ref)、浮動小数点型を生成するためのもの（`BigFloat`を除く）
  * [`Booleans`](@ref)、ブール値を生成するためのもの
  * [`Pairs`](@ref)、値のペア `a => b` を生成するためのもの
  * [`Vectors`](@ref)、`Possibility` から `Vector` を生成するためのもの
  * [`Dicts`](@ref)、キー用の `Possibility` と値用の `Possibility` から `Dict` を生成するためのもの
  * [`AsciiCharacters`](@ref)、`isascii` な `Char` を生成するためのもの
  * [`Characters`](@ref)、無効なUnicodeを含むすべての適切に形成された `Char` を生成するためのもの
  * [`UnicodeCharacters`](@ref)、無効で不正なUnicodeを含むすべての `Char` を生成するためのもの
  * [`Text`](@ref)、`Possibility{Char}` から `String` を生成するためのもの
  * [`SampledFrom`](@ref)、与えられたコレクションから値を生成するためのもの
  * [`Satisfying`](@ref)、述語を通じて `Possibility` が生成する値をフィルタリングするためのもの
  * [`Map`](@ref)、`Possibility` が生成する値に関数をマッピングするためのもの
  * [`Just`](@ref)、与えられた固定値を生成するためのもの
  * [`OneOf`](@ref)、生成するための与えられた `Possibility` の中から1つを選択するためのもの
  * [`Bind`](@ref)、他の `Possibility` の出力に `Possibility` を生成する関数をバインドするためのもの
  * [`Recursive`](@ref)、基本ケースの `Possibility` とそれを取り囲むより多くの `Possibility` をレイヤーする関数を使用して再帰的データ構造を作成するためのもの
  * [`WeightedNumbers`](@ref)、`n` の重みを与えることによって `1:n` から数をサンプリングするためのもの
  * [`WeightedSample`](@ref)、要素ごとの重みによってそのサンプリングをバイアスしながらコレクションをサンプリングするためのもの

およびこれらのユーティリティ関数：

  * `map` は `Map` を作成するためのもの
  * `filter` は `Satisfying` を作成するためのもの
  * `|` は `OneOf` を作成するためのもの
  * `bind` は `Bind` を作成するためのもの
  * `recursive` は `Recursive` を作成するためのもの
  * `Floats()` は同じ `Possibility` から `Float16`、`Float32`、`Float64` を一度に生成するためのもの
  * `BitIntegers()` は同じ `Possibility` から `Base.BitIntegers` を一度に生成するためのもの
