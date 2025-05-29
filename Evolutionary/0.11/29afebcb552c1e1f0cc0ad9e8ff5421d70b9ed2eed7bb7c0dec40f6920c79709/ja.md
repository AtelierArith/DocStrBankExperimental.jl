進化戦略の実装: (μ/ρ(+/,)λ)-ES

コンストラクタは以下のキーワード引数を取ります:

  * `initStrategy`: 初期戦略の説明 (デフォルト: 空)
  * `recombination`: 集団のためのES再結合関数 (デフォルト: `first`)、詳細は [Crossover](@ref) を参照
  * `srecombination`: 戦略のためのES再結合関数 (デフォルト: `first`)、詳細は [Crossover](@ref) を参照
  * `mutation`: 集団のための [Mutation](@ref) 関数 (デフォルト: [`nop`](@ref))
  * `smutation`: 戦略のための [Mutation](@ref) 関数 (デフォルト: [`nop`](@ref))
  * `μ`/`mu`: 親の数
  * `ρ`/`rho`: 混合数、ρ ≤ μ (すなわち、子孫の生成に関与する親の数)
  * `λ`/`lambda`: 子孫の数
  * `selection`: 選択戦略 `:plus` または `:comma` (デフォルト: `:plus`)
  * `metrics` は収束メトリックのコレクションです。
