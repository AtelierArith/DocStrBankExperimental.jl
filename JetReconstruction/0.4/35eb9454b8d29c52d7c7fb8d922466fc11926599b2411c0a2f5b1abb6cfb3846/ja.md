```
struct FinalJets
```

特定のジェット識別子に対するすべてのジェットのベクターを持つ構造体で、JSONシリアル化に使用されます。

# フィールド

  * `jetid::Int64`: ジェットのID。
  * `jets::Vector{FinalJet}`: ジェットを表す`FinalJet`オブジェクトのベクター。
