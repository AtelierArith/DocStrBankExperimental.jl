```
project(cp::CartesianProduct{N,<:Interval,<:AbstractZonotope},
        block::AbstractVector{Int};
        [kwargs...]) where {N}
```

区間とゾノトープ集合の直積の具体的な射影。

### 入力

  * `cp`    – 区間とゾノトープ集合の直積
  * `block` – ブロック構造、関心のある次元のベクトル

### 出力

`block`で指定された次元における直積`cp`の射影を表すゾノトープ。
