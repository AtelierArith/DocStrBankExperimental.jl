```
session = AzSession([; kwargs...])
```

特定の認証プロトコルを使用して認証のためのAzureセッションを作成します。 利用可能なプロトコルとその`kwargs`は以下の通りです。

## 認可コードフロー

```julia
session = AzSession(;
    protocol = _manifest["protocol"] | AzDeviceCodeFlowCredentials,
    client_id = AzSessions._manifest["client_id"],
    redirect_uri = "http://localhost:44300/reply",
    scope = "openid+offline_access+https://storage.azure.com/user_impersonation",
    scope_auth = "openid+offline_access+https://management.azure.com/user_impersonation+https://storage.azure.com/user_impersonation",
    tenant = AzSessions._manifest["tenant"],
    lazy = false,
    clearcache = false)
```

## デバイスコードフロー

```julia
session = AzSession(;
    protocol = AzDeviceCodeCredentials
    client_id = AzSessions._manifest["client_id"],
    scope = "openid+offline_access+https://management.azure.com/user_impersonation",
    scope_auth = "openid+offline_access+https://management.azure.com/user_impersonation+https://storage.azure.com/user_impersonation",
    tenant = AzSessions._manifest["tenant"],
    clearcache = false)
```

## クライアント資格情報

```julia
session = AzSession(;
    protocol = AzClientCredentials,
    tenant=AzSessions._manifest["tenant"],
    client_id=AzSessions._manifest["client_id"],
    client_secret=AzSessions._manifest["client_secret"],
    resource="https://management.azure.com/",
    clearcache = false)
```

## VM資格情報

```julia
session = AzSession(;
    protocol = AzVMCredentials,
    resource = "https://management.azure.com/",
    clearcache = false)
```

## 新しいオーディエンス

既存の認可コードフローセッションまたはデバイスコードフローセッションから新しいスコープでセッションを作成します。 これは、再認証を必要とせずに新しいオーディエンスでセッションを取得できることを意味します。 新しいスコープは`session.scope_auth`に含まれている必要があります。

```julia
session = AzSession(;
    protocol=AzAuthCodeFlowCredentials,
    scope_auth="openid+offline_access+https://management.azure.com/user_impersonation+https://storage.azure.com/user_impersonation",
    scope="openid+offline_access+https://management.azure.com/user_impersonation")

t = token(session) # `https://management.azure.com`オーディエンスのトークン
session = AzSession(session; scope="openid+offline_access+https://storage.azure.com/user_impersonation")
t = token(session) # 再認証を必要とせずに`https://storage.azure.com`オーディエンスのトークン
```

# 注意事項

  * `lazy=false`の場合、構築時に認証を行います。 そうでない場合は、セッションの最初の使用まで認証を待ちます。
  * `clearcache=false`の場合、再認証するのではなく、既存のトークンのためにセッションキャッシュをチェックします。 キャッシュはJSONファイル（`~/.azsessions/sessions.json`）に保存されます。
  * デフォルトのプロトコルはマニフェストで設定できます（詳細については`AzSessions.write_manifest`メソッドを参照してください）。
