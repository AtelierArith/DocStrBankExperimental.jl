```
truncate(population::AbstractScalarPopulation, constraint::NoConstraint)
```

`population` メンバーの要素と関連するサンプリング重みを、サンプリング `constraint` を満たすものとして取得します。

  * `constraint` が `NoConstraint` インスタンスである場合、すべてのメンバーと重みが変更されずに返されます。
