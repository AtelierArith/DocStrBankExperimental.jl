```
t8_cprofile
```

この構造体はcmeshアルゴリズムのプロファイリングに使用されます。cmesh構造体はプロファイル構造体へのポインタを格納し、非ゼロの場合、さまざまな実行時間とデータ測定がここに格納されます。

| フィールド                       | 注釈                                                  |
|:--------------------------- |:--------------------------------------------------- |
| partition*trees*shipped     | このプロセスが最後のパーティション呼び出しで他に送信したツリーの数。                  |
| partition*ghosts*shipped    | このプロセスが最後のパーティション呼び出しで他に送信したゴーストの数。                 |
| partition*trees*recv        | このプロセスが最後のパーティション呼び出しで他から受信したツリーの数。                 |
| partition*ghosts*recv       | このプロセスが最後のパーティション呼び出しで他から受信したゴーストの数。                |
| partition*bytes*sent        | このプロセスが最後のパーティション呼び出しで他のプロセスに送信したバイトの合計数。           |
| partition*procs*sent        | このプロセスが最後のパーティション呼び出しでローカルツリーまたはゴーストを送信した異なるプロセスの数。 |
| first*tree*shared           | このプロセスの最初のツリーが共有されている場合は1、そうでない場合は0。                |
| partition_runtime           | [`t8_cmesh_partition`](@ref)への最後の呼び出しの実行時間。         |
| commit_runtime              | [`t8_cmesh_commit`](@ref)への最後の呼び出しの実行時間。            |
| geometry*evaluate*num_calls | [`t8_geometry_evaluate`](@ref)への呼び出しの数。             |
| geometry*evaluate*runtime   | [`t8_geometry_evaluate`](@ref)への呼び出しの累積実行時間。        |

# 参照

[`t8_cmesh_set_profiling`](@ref)および[`t8_cmesh_print_profile`](@ref)
