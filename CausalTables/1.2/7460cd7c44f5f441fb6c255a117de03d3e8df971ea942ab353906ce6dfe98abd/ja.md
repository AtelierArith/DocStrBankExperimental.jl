```
adjacency_matrix(o::CausalTable)
```

`CausalTable`オブジェクトの`summaries`および`arrays`属性によって誘導される隣接行列を生成します。この行列は、どのユニットが互いに*因果的に依存*しているかを示します：セル(i,j)のエントリが1である場合、ユニットiの変数がユニットjの変数に因果関係を示していることを意味します。

# 引数

  * `o::CausalTable`: 隣接行列を生成するための`CausalTable`オブジェクト。

# 戻り値

`CausalTable`内の隣接関係を表すブール行列。
