```
Phase2Distribution{T} <: AbstractPhase2
```

分布から新しいデータを生成するために使用される構造体です。これは、基礎となるデータ生成プロセスを表す型 `T` のサンプル可能なフィールド `dist` を含みます。

### 注意事項

`dist` から新しいデータを生成するためには、`rand(::T)` メソッドが必要です。

### 例

```
using Distributions
DGP = Phase2Distribution(Normal(0,1))
new_data(DGP)
```
