```
automorphism_group_generators(L::AbstractLat; ambient_representation::Bool = true,
                                              depth::Int = -1, bacher_depth::Int = 0)
                                                      -> Vector{MatElem}
```

定義された格子 `L` に対して、`L` の自己同型群の生成元を返します。`ambient_representation == true`（デフォルト）であれば、変換は `L` の周囲空間に関して表現されます。そうでない場合、変換は `L` の（擬似）基底に関して表現されます。

パラメータ `depth` と `bacher_depth` を正の値に設定すると、パフォーマンスが向上する可能性があります。`-1`（デフォルト）に設定した場合、使用される `depth` の値は `L` の階数に応じてヒューリスティックに選択されます。デフォルトでは、`bacher_depth` は `0` に設定されています。
