```
diagonal_with_transform(V::AbstractSpace) -> Vector{FieldElem},
                                                         MatElem{FieldElem}
```

空間 `V` が対称空間 $\langle a_1,\dotsc,a_n \rangle$ に等長であるような要素 $a_1,\dotsc,a_n$ のベクトルを返します。第二の出力は、グラム行列が $a_i$ の対角行列であるような、`V` の直交基底を張る行を持つ行列 `U` です。

要素は `V` の固定体に含まれています。
