```
mcp_server(; name::String, version::String="2024-11-05", 
         tools::Union{Vector{MCPTool},MCPTool,Nothing}=nothing,
         resources::Union{Vector{MCPResource},MCPResource,Nothing}=nothing, 
         prompts::Union{Vector{MCPPrompt},MCPPrompt,Nothing}=nothing,
         description::String="", 
         capabilities::Vector{Capability}=default_capabilities(),
         auto_register_dir::Union{String,Nothing}=nothing) -> Server
```

モデルコンテキストプロトコル（MCP）サーバーを作成および構成するための主要なエントリーポイントです。

# 引数

  * `name::String`: サーバーインスタンスの一意の識別子
  * `version::String`: サーバー実装のバージョン
  * `tools`: モデルに公開するツール
  * `resources`: モデルが利用できるリソース
  * `prompts`: モデルのための事前定義されたプロンプト
  * `description::String`: オプションのサーバー説明
  * `capabilities::Vector{Capability}`: サーバーの能力構成
  * `auto_register_dir`: コンポーネントを自動登録するためのディレクトリ

# 戻り値

  * `Server`: MCPクライアント接続を処理する準備が整った構成済みのサーバーインスタンス

# 例

```julia
server = mcp_server(
    name = "my-server",
    description = "Demo server with time tool",
    tools = MCPTool(
        name = "get_time",
        description = "Get current time",
        parameters = [],
        handler = args -> Dates.format(now(), "HH:MM:SS")
    )
)
start!(server)
```
