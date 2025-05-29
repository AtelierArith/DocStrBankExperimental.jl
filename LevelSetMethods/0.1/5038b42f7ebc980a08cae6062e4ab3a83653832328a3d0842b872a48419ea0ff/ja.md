```
CartesianGrid(lc, hc, n)
```

下隅 `lc`、上隅 `hc` および各方向に `n` ノードを持つ均一な直交グリッドを作成します。

# 例

```jldoctest; output = true
using LevelSetMethods
a = (0, 0)
b = (1, 1)
n = (10, 4)
grid = CartesianGrid(a, b, n)

# output

CartesianGrid{2, Int64}([0, 0], [1, 1], (10, 4))
```
