```
gram_matrix_of_generators(L::AbstractLat; minimal::Bool = false) -> MatElem
```

ラティス `L` の生成集合のグラム行列を返します。

`minimal == true` の場合、最小生成集合が使用されます。最小生成子を計算するのは高コストであることに注意してください。
