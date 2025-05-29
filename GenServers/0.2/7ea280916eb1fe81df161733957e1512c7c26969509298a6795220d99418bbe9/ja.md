```
genserver(m::Module, args...; name=nothing, 
    pid=myid(), thrd=false, 
    sticky=false, taskref=nothing)
```

`:genserver` モードでアクターを作成します。メッセージを処理する際に、ユーザーが提供したモジュール `m` のコールバックを使用します。

# 引数

  * `m::Module`: 現在のスコープ内のユーザー提供モジュール、
  * `args...`: ユーザー提供の `init` コールバックへの引数。

# キーワード引数

  * `name=nothing`: `name::Symbol` が提供されると、サーバーが登録され、その名前が返されます、
  * `pid=myid()`: アクターを作成するワーカーピッド、
  * `thrd=false`: アクターを作成するスレッド、
  * `sticky=false`: `true` の場合、アクターは同じスレッドで作成されます、
  * `taskref=nothing`: `Ref{Task}` 変数が提供されると、作成された `Task` が取得されます。
