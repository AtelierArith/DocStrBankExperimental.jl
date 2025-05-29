```
generators(L::AbstractLat; minimal = false) -> Vector{Vector}
```

ラティス `L` の基底環に対する生成元の集合を返します。

`minimal == true` の場合、生成元の数は最小になります。最小生成元を計算することは高コストであることに注意してください。
