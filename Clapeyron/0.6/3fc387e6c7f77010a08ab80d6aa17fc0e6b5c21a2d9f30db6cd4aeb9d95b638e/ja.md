```
index_reduction(model::EoSModel,z,zmin = sum(z)*4*eps(eltype(z)))
index_reduction(model::EoSModel,bools <: AbstractVector{Bool})
```

成分 `z[i] < zmin` を持つ任意の成分を削除します。減少したモデル `model_r` とインデックスのベクトル `idx_r` を返します。例えば：

```julia
model_r,idx_r = index_reduction(model,z)
eos(model,V,T,z) ≈ eos(model_r,V,T,z[idx_r])
```

モデルに空の成分がない場合は、入力モデルをそのまま返します。

減少の結果が空のモデルになると、関数はエラーを返します。

任意のブールベクトル（`bools`）を渡して減少を実行できます。
