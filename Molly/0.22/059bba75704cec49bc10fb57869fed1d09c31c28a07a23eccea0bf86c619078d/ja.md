```
ImplicitSolventOBC(atoms, atoms_data, bonds)
```

Onufriev-Bashford-Case GBSAモデルがAtomsCalculators.jl計算機として実装されています。

[`Coulomb`](@ref)または[`CoulombReactionField`](@ref)相互作用と一緒に使用する必要があります。キーワード引数`use_OBC2`は、パラメータセットI（`false`、デフォルト）またはII（`true`）を使用するかどうかを決定します。
