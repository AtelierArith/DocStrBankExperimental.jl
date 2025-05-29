```
project(cp::CartesianProduct{N,<:Interval,<:AbstractHyperrectangle},
        block::AbstractVector{Int};
        [kwargs...]) where {N}
```

区間と超長方形のデカルト積の具体的な射影。

### 入力

  * `cp`    – 区間と超長方形のデカルト積
  * `block` – ブロック構造、関心のある次元を持つベクトル

### 出力

`block`で指定された次元におけるデカルト積`cp`の射影を表す超長方形。
