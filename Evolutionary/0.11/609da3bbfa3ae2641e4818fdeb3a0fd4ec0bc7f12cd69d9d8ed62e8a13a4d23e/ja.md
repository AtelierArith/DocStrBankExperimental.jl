非支配ソート遺伝アルゴリズム (NSGA-II) による多目的最適化

コンストラクタは以下のキーワード引数を取ります：

  * `populationSize`: 集団のサイズ
  * `crossoverRate`: 次世代の集団のうち、交差関数によって生成される割合
  * `mutationRate`: 染色体が突然変異する確率
  * `selection`: [Selection](@ref) 関数 (デフォルト: `tournament`)
  * `crossover`: [Crossover](@ref) 関数 (デフォルト: `SBX`)
  * `mutation`: [Mutation](@ref) 関数 (デフォルト: `PLM`)
  * `metrics` は収束メトリクスのコレクションです。
