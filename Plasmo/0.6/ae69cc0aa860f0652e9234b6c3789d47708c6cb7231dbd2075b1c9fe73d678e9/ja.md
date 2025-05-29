```
graph_index(
    backend::GraphMOIBackend, 
    ref::RT
) where {RT<:Union{NodeVariableRef,ConstraintRef}}
```

バックエンドモデルの実際の変数または制約インデックスを返します。これは、ノードまたはエッジのローカルインデックスに対応します。
