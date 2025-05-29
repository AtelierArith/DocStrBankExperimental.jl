```
JointStratifiedCV(;patterns=nothing, resampling=StratifiedCV())
```

Xとyから構築された変数に基づいて層化交差検証戦略を適用します。次のような合成変数が構築されます：

  * `patterns`のいずれかに一致し、`autotype(x) <: Union{Missing, Finite}`を満たすXからのx変数。

パターンが提供されていない場合、2番目の条件のみが考慮されます。

  * `autotype(y) <: Union{Missing, Finite}`の場合のy

`resampling`は層化に準拠した再サンプリング戦略である必要があり、現在は`StratifiedCV`または`AdaptiveStratifiedCV`のいずれかです。
