```
reset_aggregated_jumps!(integrator, uprev = nothing; update_jump_params=true)
```

ジャンププロセスと関連するソルバーの状態を、パラメータの変更などに従ってリセットします。

ノート

  * `update_jump_params=true` は、パラメータベクトルから構築された任意のMassActionJump内に保存されたレートを再計算します。パラメータベクトルが変更されていない場合、パフォーマンスを向上させるために安全にfalseに設定できます。
