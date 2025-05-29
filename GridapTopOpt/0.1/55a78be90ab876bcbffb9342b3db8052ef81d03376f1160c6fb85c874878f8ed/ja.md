```
update_labels!(e::Int,model,f_Γ::Function,name::String)
```

タグ番号 `e`、`CartesianDiscreteModel` または `DistributedDiscreteModel` モデル、指標関数 `f_Γ`、および文字列 `name` を与えると、対応する頂点、エッジ、および面に `name` としてラベルを付けます。

注意: `f_Γ` はベクトルを受け取り、Γ を示すかどうかに応じてブール値を返さなければなりません。
