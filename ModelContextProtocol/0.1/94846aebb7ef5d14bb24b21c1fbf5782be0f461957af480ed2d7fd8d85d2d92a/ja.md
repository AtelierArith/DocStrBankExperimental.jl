```
register!(server::Server, component::Union{Tool,Resource,MCPPrompt}) -> Server
```

MCPサーバーにツール、リソース、またはプロンプトを登録します。

# 引数

  * `server::Server`: コンポーネントを登録するサーバー
  * `component`: 登録するコンポーネント（ツール、リソース、またはプロンプトのいずれか）

# 戻り値

  * `Server`: メソッドチェイニングのためのサーバーインスタンス
