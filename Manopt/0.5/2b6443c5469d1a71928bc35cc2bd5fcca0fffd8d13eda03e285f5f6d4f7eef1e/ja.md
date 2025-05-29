```
get_equality_constraint(M::AbstractManifold, emo::EmbeddedManifoldObjective, p, j)
```

埋め込みで定義された `j` の等式制約 $h_j(p)$ を評価します。つまり、[`EmbeddedManifoldObjective`](@ref) に格納された制約関数を呼び出す前に `p` を埋め込みます。
