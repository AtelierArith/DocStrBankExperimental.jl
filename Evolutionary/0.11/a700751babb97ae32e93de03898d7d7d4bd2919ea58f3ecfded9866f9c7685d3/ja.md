Differential Evolutionの実装: DE/**selection**/n/**recombination**

コンストラクタは以下のキーワード引数を取ります:

  * `populationSize`: 集団のサイズ
  * `F`: 差分（変異）スケールファクター（デフォルト: 0.9）。通常、範囲 $F \in (0, 1+]$ で定義されます
  * `n`: 摂動に使用される差分の数（デフォルト: 1）
  * `selection`: 選択戦略関数（デフォルト: [`random`](@ref)）
  * `recombination`: 再結合関数（デフォルト: [`BINX(0.5)`](@ref)）
  * `K`: 再結合スケールファクター（デフォルト: 0.5*(F+1)）
  * `metrics` は収束メトリクスのコレクションです。
