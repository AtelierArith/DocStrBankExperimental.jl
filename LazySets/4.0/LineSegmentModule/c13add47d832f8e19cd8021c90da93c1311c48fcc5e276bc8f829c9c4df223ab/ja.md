# 拡張ヘルプ

```
constraints_list(L::LineSegment)
```

### アルゴリズム

$$
L
$$

は 4 つの制約によって定義されます。このアルゴリズムでは、最初の 2 つの制約は `halfspace_right` と `halfspace_left` によって返され、残りの 2 つは、頂点の 1 つを通る線分に平行なベクトルを考慮することによって得られます。
