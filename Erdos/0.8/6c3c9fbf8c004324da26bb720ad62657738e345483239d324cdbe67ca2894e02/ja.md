```
dismantle_ci_oneiter!(g, heap, lneigs, l)
```

[`dismantle_ci`](@ref)アルゴリズムの1ステップ。[`dismantle_ci_init`](@ref)の後に呼び出されます。クリーンアップされた頂点があれば返し（[`clean_vertex!`](@ref）を参照）、そうでなければ-1を返します。
