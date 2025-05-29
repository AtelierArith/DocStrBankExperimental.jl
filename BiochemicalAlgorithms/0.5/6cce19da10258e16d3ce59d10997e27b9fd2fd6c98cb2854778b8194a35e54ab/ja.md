```
optimize_structure!(ff::ForceField)
```

与えられたフォースフィールドオブジェクトによって表されるエネルギー最適化問題を解決しようとします。

# サポートされているキーワード引数

この関数はすべてのキーワード引数を [Optimization.solve](https://docs.sciml.ai/Optimization/stable/API/solve/) に渡し、以下のデフォルト値を持ちます：

  * `alg = Optimization.LBFGS()`
