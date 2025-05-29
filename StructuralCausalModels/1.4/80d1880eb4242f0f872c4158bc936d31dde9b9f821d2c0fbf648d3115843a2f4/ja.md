# ancestral_graph

```julia
ancestral_graph(d; m, c)

```

周辺化と条件付けの後の祖先グラフ。

### 必要な引数

```julia
* `d::DAG`                             : DAGオブジェクト
```

### オプションの引数

```julia
* `m::Vector{Symbol}`                  : 周辺化されるDAGのノード
* `c::Vector{Symbol})`                 : 条件付けされるDAGのノード
```

### 戻り値

```julia
* `ag::NamedArray`                     : 残りの祖先グラフ
```
