```
container = AzContainer("containername"; storageaccount="myacccount", kwargs...)
```

`container` は `myaccount` ストレージアカウント内の新しいまたは既存の Azure コンテナへのハンドルです。ストレージアカウントはすでに存在している必要があります。

# 追加のキーワード引数

  * `session=AzSession(;lazy=false,scope=offline_access+openid+https://storage.azure.com/user_impersonation)` ユーザー認証情報（AzSessions.jl パッケージを参照）。
  * `nthreads=Sys.CPU_THREADS` OpenMP が I/O をスレッド化するために使用するシステムスレッドの数。
  * `connect_timeout=30` サーバーへの接続のためのクライアント側のタイムアウト。
  * `read_timeout=10` サーバーから最初のバイトを受信するためのクライアント側のタイムアウト。
  * `nretry=10` Azure サービスへの再試行の回数（Azure が再試行可能なエラーをスローした場合）で、エラーをスローする前に。
  * `verbose=0` libcurl に渡される冗長性フラグ。

# 注意事項

コンテナ名には "/" を含めることができます。この場合、最初の "/" の前の文字列がコンテナ名となり、残りの文字列が blob 名の前に追加されます。これにより、Azure は擬似ディレクトリ構造で blob を表示できます。末尾および先頭の "/" は無視されることに注意してください。
