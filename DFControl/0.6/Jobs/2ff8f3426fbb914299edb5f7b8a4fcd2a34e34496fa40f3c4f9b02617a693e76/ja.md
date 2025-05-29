```
set_flow!(job::Job, should_runs::Pair{String, Bool}...)
```

計算が実行されるべきかどうかを設定します。ジョブ内の各計算の`name`は、各`should_runs`のペア内の文字列と照合され、`calculation.run`がそれに応じて設定されます。

例:

```julia
set_flow!(job, "" => false, "scf" => true)
```

は、ジョブ内のすべての計算のスケジュールを解除し、"scf"および"nscf"計算を実行するようにスケジュールします。
