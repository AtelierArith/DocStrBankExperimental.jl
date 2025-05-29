```julia
mutable struct AlgorithmLogData
```

アルゴリズムログファイルから読み取ったデータを格納します。1つの解法プロセスからプロットを生成するために使用できます。

# フィールド

  * `totalIterations::Vector{Union{Missing, Int64}}`: 各イテレーションの総イテレーション数の実行番号。
  * `sections::Vector{String}`: 各イテレーションのセクションタグ。
  * `partIterations::Vector{Union{Missing, Int64}}`: 各イテレーションの現在のセクションでのイテレーション数の実行番号。
  * `types::Vector{Union{Missing, String}}`: 各イテレーションの更新ステップのタイプのタグ。長いおよび適応的なステッピングスキームにのみ関連します。
  * `lastaccepts::Vector{Union{Missing, Int64}}`: 各イテレーションの前回の受け入れからのイテレーション数。適応的なステッピングスキームにのみ関連します。
  * `kappas::Vector{Union{Missing, Float64}}`: 各イテレーションのパラメータkappa。適応的なステッピングスキームにのみ関連します。
  * `accnorms::Vector{Union{Missing, Float64}}`: 各イテレーションのステップの受け入れのためのノルム値。長いおよび適応的なステッピングスキームにのみ関連します。
  * `searchIterations::Vector{Union{Missing, Int64}}`: 各イテレーションのバックトラッキングラインサーチでのイテレーション数。長いおよび適応的なステッピングスキームにのみ関連します。
  * `scalings::Vector{Union{Missing, Float64}}`: 各イテレーションのバックトラッキングによって生成された更新のスケーリング。長いおよび適応的なステッピングスキームにのみ関連します。
  * `ts::Vector{Union{Missing, Float64}}`: 各イテレーションのtの値。
  * `criteria::Vector{Union{Missing, Float64}}`: 各イテレーションの収束基準の値。
  * `bounds::Vector{Union{Missing, Float64}}`: 各イテレーションの収束基準の境界。セクションごとに一定です。
  * `conditions::Vector{Union{Missing, Float64}}`: 各イテレーションのシステム行列の条件数。
