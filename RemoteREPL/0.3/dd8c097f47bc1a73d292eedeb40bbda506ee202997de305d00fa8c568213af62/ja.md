```
connect_repl([host=localhost,] port::Integer=27754;
             tunnel = (host != localhost) ? :ssh : :none,
             ssh_opts = ``, region=nothing, namespace=nothing,
             repl=Base.active_repl, session_id = nothing)
```

リモート `host` の `port` にクライアント REPL を接続します。これにより、現在の Julia セッションのリモートサブ REPL としてアクセス可能になります。

セキュリティのために、`connect_repl()` はリモートホストに対して ssh トンネルを使用します。これは、`host` が ssh サーバーを実行している必要があり、そのホストで使用するための ssh 認証情報が設定されている必要があることを意味します。セキュアなネットワークでは、`tunnel=:none` を設定することでこれを無効にできます。

SSH に追加のオプションを提供するには、`ssh_opts` キーワードに `Cmd` オブジェクトを渡すことができます。たとえば、アイデンティティファイルは ```ssh_opts = `-i /path/to/identity.pem` ``` で設定できます。より永続的な解決策として、ssh 設定ファイルに `Host` セクションを追加してください。

SSH の代わりにトンネリングに次の技術を使用することもできます：

1. AWS セッションマネージャー：`tunnel=:aws` を設定します。オプションの `region` キーワード引数を使用して、サーバーの AWS リージョンを指定できます。
2. kubectl：`tunnel=:k8s` を設定します。オプションの `namespace` キーワード引数を使用して、Kubernetes リソースの名前空間を指定できます。

詳細については README.md を参照してください。
