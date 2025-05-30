```
DifferentiationBenchmarkDataRow
```

微分ベンチマーキング結果のためのアドホックストレージタイプ。

# フィールド

  * `backend::ADTypes.AbstractADType`: ベンチマーキングに使用されるバックエンド
  * `scenario::DifferentiationInterfaceTest.Scenario`: ベンチマーキングに使用されるシナリオ
  * `operator::Symbol`: ベンチマーキングに使用される微分演算子、例: `:gradient` または `:hessian`
  * `prepared::Union{Nothing, Bool}`: 演算子が準備されていたかどうか
  * `calls::Int64`: 演算子への1回の呼び出しに対する微分された関数への呼び出し回数
  * `samples::Int64`: 取得されたベンチマーキングサンプルの数
  * `evals::Int64`: 各サンプルで平均化に使用される評価の数
  * `time::Any`: すべてのサンプルにわたる集計実行時間（秒）
  * `allocs::Any`: すべてのサンプルにわたる集計アロケーション数
  * `bytes::Any`: すべてのサンプルにわたる集計メモリ使用量（バイト）
  * `gc_fraction::Any`: すべてのサンプルにわたるガーベジコレクションに費やされた時間の集計割合（0.0から1.0の間）
  * `compile_fraction::Any`: すべてのサンプルにわたるコンパイルに費やされた時間の集計割合（0.0から1.0の間）

測定フィールドの詳細については、[Chairmarks.jl](https://github.com/LilithHafner/Chairmarks.jl)のドキュメントを参照してください。
