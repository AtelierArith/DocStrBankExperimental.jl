```julia
export_realized_results(
    res::InfrastructureSystems.Results
) -> String

```

すべての変数、パラメータ、双対、補助変数、式、および最適化統計の実現結果をCSVファイルに保存します。

# 引数

  * `res::Results`: 結果
  * `save_path::AbstractString` : 結果を保存するパス（デフォルトはシミュレーションパス）
