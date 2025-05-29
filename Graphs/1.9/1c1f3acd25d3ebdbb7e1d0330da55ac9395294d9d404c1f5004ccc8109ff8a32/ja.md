```
weights(g)
```

グラフ `g` のエッジの重みを行列として返します。デフォルトは [`Graphs.DefaultDistance`](@ref) です。

### 実装ノート

一般に、存在しないエッジの重みを参照することは未定義の動作です。グラフの [`adjacency_matrix`](@ref) の代わりに `weights` 行列に依存しないでください。
