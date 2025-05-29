```
BigM{T} <: AbstractReformulationMethod
```

不等式制約のためのビッグ-M再定式化アプローチを使用するための型です。

**フィールド**

  * `value::T`: ビッグ-M値（デフォルト = `1e9`）。
  * `tight::Bool`: ビッグ-M値を引き締めることを試みるか（デフォルト = `true`）？
