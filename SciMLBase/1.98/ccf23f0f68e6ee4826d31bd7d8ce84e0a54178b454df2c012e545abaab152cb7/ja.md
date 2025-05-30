```julia
struct CallbackSet{T1<:Tuple, T2<:Tuple} <: SciMLBase.DECallback
```

複数のコールバックを連結して `CallbackSet` を形成することができます。`CallbackSet` は、コンストラクタ `ContinuousCallback`、`DiscreteCallback`、`VectorContinuousCallback` または他の `CallbackSet` インスタンスを渡すことによって構築されます：

```
CallbackSet(cb1,cb2,cb3)
```

好きなだけコールバックを渡すことができます。ソルバーが複数のコールバックに遭遇した場合、次のルールが適用されます：

  * `ContinuousCallback` と `VectorContinuousCallback` は `DiscreteCallback` の前に適用されます。（これは、これらがしばしばイベント検出を実装しており、タイムステップを `dt` よりも小さく戻すためです）。
  * `ContinuousCallback` と `VectorContinuousCallback` の場合、イベント時間はルートファインディングによって見つけられ、最初の `ContinuousCallback` または `VectorContinuousCallback` の影響のみが適用されます。
  * 次に、`DiscreteCallback` が順番に適用されます。条件に関してのみ順序が重要であることに注意してください：前のコールバックが `u` を変更し、次のコールバックが条件を `true` と評価しなくなった場合、その `affect` は適用されません。
