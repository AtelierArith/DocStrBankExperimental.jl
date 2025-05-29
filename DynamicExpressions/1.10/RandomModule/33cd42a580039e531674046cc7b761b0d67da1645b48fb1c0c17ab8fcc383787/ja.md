```
NodeSampler(; tree, filter::Function=Returns(true), weighting::Union{Nothing,Function}=nothing, break_sharing::Val=Val(false))
```

木のノードのサンプラーを定義します。

# 引数

  * `tree`: ノードをサンプリングする木。通常の `Node` では、ノードは均等にサンプリングされます。`GraphNode` の場合もノードは均等にサンプリングされます（例：`sin(x) + {x}` では、`x` は `sin` または `+` ノードからサンプリングされる確率が等しいため、共有されています）、ただし `break_sharing` が `Val(true)` に設定されている場合を除きます。
  * `filter::Function`: ノードを受け取り、そのノードをサンプリングするべきかどうかを示すブール値を返す関数。デフォルトは `Returns(true)` です。
  * `weighting::Union{Nothing,Function}`: ノードを受け取り、フィルターを通過した場合にそのノードの重みを返す関数。ノードのサンプリング確率に比例します。`nothing` の場合、すべてのノードは均等にサンプリングされます。
  * `break_sharing::Val`: `Val(true)` の場合、サンプラーは木の共有を破り、木から均等にノードをサンプリングします。
