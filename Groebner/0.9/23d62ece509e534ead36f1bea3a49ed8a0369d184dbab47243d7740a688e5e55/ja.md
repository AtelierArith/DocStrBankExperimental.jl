```
WeightedOrdering(weights)
```

重み付きモノミアル順序。

正の重みのみがサポートされています。

## 例

```@example
using Groebner, AbstractAlgebra
R, (x, y) = QQ["x", "y"];

# xの重みは3、yの重みは1
ord = WeightedOrdering(x => 3, y => 1)
groebner([x*y + x, x + y^2], ordering=ord)
```
