```
Server(name                ::String,
       username            ::String,
       domain              ::String,
       scheduler           ::Scheduler,
       julia_exec          ::String,
       jobdir              ::String,
       max_concurrent_jobs ::Int)
Server(name::String)
```

A [`Server`](@ref) は、ローカルまたはリモートクラスター上で実行されるデーモンを表します。これは、HPCジョブを保存、提出、監視、および取得するために必要なすべてのリモート操作を容易にします。

他の[`Storable`](@ref)と同様に、`name`は単にラベルとして使用されます。

`username`と`domain`は、ローカルマシンとリモートホスト間で`ssh`接続を許可するものである必要があります。`ssh`コマンドを実行するためにパスワードが必要ないことを確認してください。つまり、`ssh-copy-id`を使用して`ssh`キーをコピーしておく必要があります。

`julia_exec`は、リモートホスト上で`julia`実行可能ファイルを見つけるためのパスである必要があります。`scheduler`は自動的に推測されますが、必要に応じて上書きすることができます。
