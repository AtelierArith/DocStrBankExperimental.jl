```julia
AdjacencyMatrix(
    branches,
    buses;
    check_connectivity,
    kwargs...
)

```

バスとブランチのコレクションから隣接行列を構築します。返されるのは、バス番号でインデックス付けされた N x N 隣接行列配列です。

# 引数

  * `check_connectivity::Bool`:       深さ優先探索 (DFS) アルゴリズムを使用してネットワークの接続性をチェックします。
