```
is_isometric_with_isometry(L::AbstractLat, M::AbstractLat; ambient_representation::Bool = true
                                                           depth::Int = -1, bacher_depth::Int = 0)
                                                          -> (Bool, MatElem)
```

格子 `L` と `M` が同型であるかどうかを返します。もしそうであれば、2番目に返される値は `L` から `M` への同型写像 `T` です。

デフォルトでは、その同型写像は周囲空間の基底に関して表現されます。すなわち、$T V_M T^t = V_L$ であり、ここで $V_L$ と $V_M$ はそれぞれ `L` と `M` の周囲空間のグラム行列です。もし `ambient_representation == false` の場合、同型写像は `L` と `M` の（擬似）基底に関して表現されます。すなわち、$T G_M T^t = G_L$ であり、ここで $G_M$ と $G_L$ はそれぞれ `L` と `M` の（擬似）基底のグラム行列です。

パラメータ `depth` と `bacher_depth` を正の値に設定すると、パフォーマンスが向上する可能性があります。`-1`（デフォルト）に設定されている場合、使用される `depth` の値は `L` の階数に応じてヒューリスティックに選択されます。デフォルトでは、`bacher_depth` は `0` に設定されています。
