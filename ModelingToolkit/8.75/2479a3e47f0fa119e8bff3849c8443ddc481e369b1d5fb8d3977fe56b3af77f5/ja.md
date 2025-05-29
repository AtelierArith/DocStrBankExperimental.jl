```
getbounds(sys::ModelingToolkit.AbstractSystem, p = parameters(sys))
```

`sys`のパラメータを下限と上限にマッピングするペア`p => (lb, ub)`を持つ辞書を返します。次のようにして境界を持つパラメータを作成します。

```
@parameters p [bounds=(-1, 1)]
```

状態の境界を取得するには、`getbounds(sys, states(sys))`を呼び出します。
