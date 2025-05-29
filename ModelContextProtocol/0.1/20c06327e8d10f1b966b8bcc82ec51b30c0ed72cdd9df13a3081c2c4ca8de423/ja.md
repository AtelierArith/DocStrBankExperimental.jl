```
Server(config::ServerConfig)
```

リソース、ツール、およびプロンプトを管理する実行中のMCPサーバーインスタンスを表します。

# フィールド

  * `config::ServerConfig`: サーバー設定
  * `resources::Vector{Resource}`: 利用可能なリソース
  * `tools::Vector{Tool}`: 利用可能なツール
  * `prompts::Vector{MCPPrompt}`: 利用可能なプロンプト
  * `resource_templates::Vector{ResourceTemplate}`: 利用可能なリソーステンプレート
  * `subscriptions::DefaultDict{String,Vector{Subscription}}`: リソースサブスクリプションレジストリ
  * `progress_trackers::Dict{Union{String,Int},Progress}`: 操作の進捗追跡
  * `active::Bool`: サーバーが現在アクティブかどうか

# コンストラクタ

  * `Server(config::ServerConfig)`: 指定された設定で新しいサーバーを作成します。
