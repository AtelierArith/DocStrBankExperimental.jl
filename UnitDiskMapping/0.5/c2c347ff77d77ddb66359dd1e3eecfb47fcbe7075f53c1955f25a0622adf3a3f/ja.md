```
map_qubo_square(coupling::AbstractVector, onsite::AbstractVector) -> SquareQUBOResult
```

正方格格子上のQUBO問題を、グリッドグラフ上の重み付きMIS問題にマッピングします。QUBO問題は以下のように指定できます。

  * ベクトル結合 `(i, j, i', j', J)`、ただし (i', j') == (i, j+1) または (i', j') = (i+1, j)。
  * 現場項のベクトル `(i, j, h)`。

$$
E(z) = -\sum_{(i,j)\in E} J_{ij} z_i z_j + h_i z_i
$$

正方格子QUBO問題のガジェットは以下の通りです。

```
⋅ ⋅ ⋅ ⋅ ● ⋅ ⋅ ⋅ ⋅ 
○ ⋅ ● ⋅ ⋅ ⋅ ● ⋅ ○ 
⋅ ⋅ ⋅ ● ⋅ ● ⋅ ⋅ ⋅ 
⋅ ⋅ ⋅ ⋅ ○ ⋅ ⋅ ⋅ ⋅ 
```

白い円は重み1、黒い円は重み2を持ちます。単位距離は `2.3` です。
