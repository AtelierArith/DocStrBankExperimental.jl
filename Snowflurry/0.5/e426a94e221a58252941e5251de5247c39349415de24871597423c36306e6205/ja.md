```
クライアント
```

QPUサービスへの接続のための*クライアント*を表すデータ構造。  

# フィールド

  * `host::String` – QPUサーバーのURL。
  * `user::String` – ユーザー名。
  * `access_token::String` – ユーザーアクセス トークン。
  * `realm::String` – オプション: リクエストの送信のためにホストサーバーのレルムを識別するために使用されます。

# 例

```jldoctest
julia> c = Client(
            host = "http://example.anyonsys.com",
            user = "test_user",
            access_token = "not_a_real_access_token",
            realm = "test_realm"
        )
Client for QPU service:
   host:         http://example.anyonsys.com
   user:         test_user 
   realm:        test_realm 
 
```
