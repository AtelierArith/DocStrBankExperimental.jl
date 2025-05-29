```
t8_profile
```

| フィールド                      | 注釈                                                                                          |
|:-------------------------- |:------------------------------------------------------------------------------------------- |
| partition*elements*shipped | このプロセスが最後のパーティション呼び出しで他のプロセスに送信した要素の数。                                                      |
| partition*elements*recv    | このプロセスが最後のパーティション呼び出しで他のプロセスから受信した要素の数。                                                     |
| partition*bytes*sent       | 最後のパーティション呼び出しで他のプロセスに送信されたバイトの合計数。                                                         |
| partition*procs*sent       | このプロセスが最後のパーティション呼び出しでローカル要素を送信した異なるプロセスの数。                                                 |
| ghosts_shipped             | このプロセスが他のプロセスに送信したゴースト要素の数。                                                                 |
| ghosts_received            | このプロセスが他のプロセスから受信したゴースト要素の数。                                                                |
| ghosts_remotes             | このプロセスがゴースト要素を送信した（および受信した）プロセスの数。                                                          |
| balance_rounds             | バランス中の反復回数。                                                                                 |
| adapt_runtime              | [`t8_forest_adapt`](@ref) への最後の呼び出しの実行時間（[`t8_forest_balance`](@ref) での適応はカウントしない）。         |
| partition_runtime          | [`t8_cmesh_partition`](@ref) への最後の呼び出しの実行時間（[`t8_forest_balance`](@ref) でのパーティションはカウントしない）。 |
| ghost_runtime              | [`t8_forest_ghost_create`](@ref) への最後の呼び出しの実行時間。                                            |
| ghost_waittime             | ゴーストでの同期時間の量。                                                                               |
| balance_runtime            | [`t8_forest_balance`](@ref) への最後の呼び出しの実行時間。                                                 |
| commit_runtime             | [`t8_cmesh_commit`](@ref) への最後の呼び出しの実行時間。                                                   |
