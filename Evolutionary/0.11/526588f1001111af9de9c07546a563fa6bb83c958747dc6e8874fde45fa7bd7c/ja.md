Koza型（木構造）遺伝的プログラミングの実装

コンストラクタは以下のキーワード引数を受け取ります：

  * `populationSize`: 集団のサイズ
  * `terminals`: 対応する次元を持つ端末の辞書

      * この辞書は（`Terminal`, `Int`）のペアを含みます
      * 端末は任意の記号（変数）、定数値、または0引数関数であることができます。
  * `functions`: 対応する引数の数を持つ関数のコレクション。

      * この辞書は（`Function`, `Int`）のペアを含みます
  * `initialization`: 集団初期化の戦略（デフォルト: `:grow`）

      * 可能な値: `:grow` と `:full`
  * `mindepth`: 式の最小深さ（デフォルト: `0`）
  * `maxdepth`: 式の最大深さ（デフォルト: `3`）
  * `mutation`: 突然変異関数（デフォルト: [`crosstree`](@ref)）
  * `crossover`: 交差関数（デフォルト: [`subtree`](@ref)）
  * `simplify`: 式の簡略化関数（デフォルト: `:nothing`）
  * `optimizer`: 式を進化させるために使用される進化的最適化器（デフォルト: [`GA`](@ref)）

      * `mutation` と `crossover` パラメータを使用して、GP関連の突然変異操作を指定します。
      * `selection` パラメータを使用して、子孫選択手続きを指定します。
