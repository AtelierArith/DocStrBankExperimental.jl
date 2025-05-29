```
get_inequality_constraint(M::AbstractManifold, ems::EmbeddedManifoldObjective, p, i)
```

埋め込みで定義された `i` の不等式制約 $g_i(p)$ を評価します。つまり、[`EmbeddedManifoldObjective`](@ref) に格納された制約関数を呼び出す前に `p` を埋め込みます。
