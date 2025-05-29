```
unsubscribe(client::ShadowClient)
```

すべてのシャドウドキュメントトピックの購読を解除します。

引数:

  * `client (ShadowClient)`: 使用するシャドウクライアント。

各 [`unsubscribe`](@ref) 呼び出しが完了すると、完了するタスクを返します。また、各 [`unsubscribe`](@ref) 呼び出しからのパケットIDを含むコレクションも返します。
