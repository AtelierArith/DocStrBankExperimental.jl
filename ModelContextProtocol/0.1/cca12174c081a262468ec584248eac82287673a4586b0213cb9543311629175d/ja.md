```
ServerConfig(; name::String, version::String="1.0.0", 
           description::String="", capabilities::Vector{Capability}=Capability[],
           instructions::String="")
```

MCPサーバーインスタンスの設定を定義します。

# フィールド

  * `name::String`: クライアントに表示されるサーバー名
  * `version::String`: サーバーバージョン文字列
  * `description::String`: 人間が読めるサーバーの説明
  * `capabilities::Vector{Capability}`: サーバーがサポートするプロトコル機能
  * `instructions::String`: クライアント向けの使用指示
