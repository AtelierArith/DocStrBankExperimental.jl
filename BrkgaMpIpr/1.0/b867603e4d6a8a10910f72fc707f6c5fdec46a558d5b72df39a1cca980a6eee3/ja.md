```
mutable struct BrkgaParams
```

BRKGAおよびIPRのハイパーパラメータを表します。これらのパラメータは、[`load_configuration`](@ref)および[`build_brkga`](@ref)を使用して構成ファイルから読み込むことができ、[`write_configuration`](@ref)を使用して書き込むことができます。

## フィールド

  * `population_size`: 集団の要素数 [> 0]。
  * `elite_percentage`: エリートセットになる個体の割合 (0, 1]。
  * `mutants_percentage`: 集団に挿入される突然変異体の割合。
  * `num_elite_parents`: 交配のためのエリート親の数 [> 0]。
  * `total_parents`: 交配のための総親の数 [> 0]。
  * `bias_type`: 使用されるバイアスタイプ。
  * `num_independent_populations`: 独立した並行集団の数。
  * `pr_number_pairs`: パスリリンクのためにテストされる染色体のペアの数。
  * `pr_minimum_distance`: パスリリンクのために選択された染色体間の最小距離。
  * `pr_type`: パスリリンクのタイプ。
  * `pr_selection`: パスリリンクのための個体選択。
  * `alpha_block_size`: 集団のサイズに基づいてブロックサイズを定義します。
  * `pr_percentage`: 計算されるパーセンテージ / パスサイズ。値は (0, 1] の範囲です。
