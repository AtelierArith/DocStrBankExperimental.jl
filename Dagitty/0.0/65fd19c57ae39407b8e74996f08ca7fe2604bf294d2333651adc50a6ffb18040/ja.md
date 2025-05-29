```
is_d_separated(dag, x, y, cond)
```

X変数が第三の変数のセットに条件付けられたY変数に対して独立であることを確認します。三つのセットはノードラベル（`Symbol`）のベクトルまたは基盤となるグラフのノードインデックスのベクトルとして与えることができます。NetworkXの`d_separated`実装を使用しています。

# 例

```jldoctest
julia> using Dagitty

julia> g = DAG(:A => :C, :C => :B)
DAG: {3, 2} directed simple Int64 graph with labels [:A, :B, :C])

julia> is_d_separated(g, [:A], [:B], [:C])
true

julia> is_d_separated(g, [:A], [:C], [:B])
false

julia> is_d_separated(g, [1], [2], [3])
true
```
