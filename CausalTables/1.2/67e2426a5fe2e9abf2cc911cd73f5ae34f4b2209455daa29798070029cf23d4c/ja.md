```
struct StructuralCausalModel
```

構造的因果モデル (SCM) を表す構造体です。これにはデータ生成プロセスが含まれます。

# 引数

  * `dgp::DataGeneratingProcess`: ランダムデータが抽出されるデータ生成プロセス。
  * `treatment::Vector{Symbol}`: 処置を表す変数。
  * `response::Vector{Symbol}`: 応答を表す変数。
  * `causes::Union{NamedTuple, Nothing}`: データ生成プロセスにおける関連変数の原因をラベル付けするベクトルの NamedTuple。`nothing` の場合、`treatment` または `response` に含まれないすべての変数が両方の共通原因であると仮定します。
  * `arraynames`: "表形式" 変数として含まれていないデータ生成プロセスで使用される補助変数の名前。主に、前のステップの要約関数を計算するために使用される隣接行列の名前を示すために使用されます。
