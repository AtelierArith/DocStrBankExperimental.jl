遺伝的アルゴリズムの実装

コンストラクタは以下のキーワード引数を取ります：

  * `populationSize`: 集団のサイズ
  * `crossoverRate`: エリートの子供を除く次世代の集団の割合で、交差関数によって作成されるもの。
  * `mutationRate`: 染色体が突然変異する確率
  * `ɛ`/`epsilon`: 現在の世代で次の世代に生き残ることが保証されている個体の数を指定する正の整数。浮動小数点数は集団の割合を指定します。
  * `selection`: [Selection](@ref) 関数（デフォルト: [`tournament`](@ref)）
  * `crossover`: [Crossover](@ref) 関数（デフォルト: [`genop`](@ref)）
  * `mutation`: [Mutation](@ref) 関数（デフォルト: [`genop`](@ref)）
  * `metrics` は収束メトリックのコレクションです。
