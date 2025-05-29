この関数は分布の数値サポートを表し、タプル `(float_start::Float, float_stop::Float)` を返します。デフォルト値は `(1e-4, 10_000)` です。いくつかの分布は `0` で定義されていないことに注意してください。例えば、形状パラメータが1未満のワイブル分布です。

pdfとハザードは `float_start` の前で0であり、`cumulative_hazard` でハザードの積分を計算するための数値積分は `beginning` から始まります。`rand` でサンプリングする際には、サポート上でODEが解かれます。

# 使用法

データに応じてサポートを調整する必要があります。

```julia
JointSurvivalModels.support(dist:HazardBasedDistribution) = (-100, 1000)
```
