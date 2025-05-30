```
reset_aggregated_jumps!(integrator, uprev = nothing; update_jump_params=true)
```

パラメータの変更などに従って、ジャンププロセスと関連するソルバーの状態をリセットします。

ノート

  * `update_jump_params=true` は、パラメータベクトルから構築された任意の MassActionJump 内に保存されたレートを再計算します。パラメータベクトルが変更されていない場合、パフォーマンスを向上させるために安全に false に設定できます。
