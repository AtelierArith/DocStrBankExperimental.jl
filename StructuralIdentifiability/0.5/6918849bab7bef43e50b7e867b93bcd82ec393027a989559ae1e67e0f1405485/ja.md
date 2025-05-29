```
macro DDSmodel
```

DDS（離散動的システム）を方程式のリストから作成するためのマクロです。また、すべての変数をグローバルスコープに注入します。

## 例

シンプルな `DDS` を作成する：

```jldoctest
using StructuralIdentifiability

dds = @DDSmodel(
    x1(t + 1) = a * x1(t) + u(t),
    x2(t + 1) = b * x2(t) + c*x1(t)*x2(t),
    y(t) = x1(t)
)
```

ここで、

  * `x1`, `x2` は状態変数です
  * `y` は出力変数です
  * `u` は入力変数です
  * `a`, `b`, `c` は時間に依存しないパラメータです
