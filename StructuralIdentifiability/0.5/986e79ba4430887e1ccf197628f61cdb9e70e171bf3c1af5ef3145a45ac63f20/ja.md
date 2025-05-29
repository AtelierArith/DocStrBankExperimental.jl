```
find_ioequations(ode, [var_change_policy=:default])
```

ODEシステムの入力-出力方程式を見つけます 入力:

  * `ode` - ODEシステム
  * `var_change_policy` - 自動変数変更を行うかどうか、`:default`、`:yes`、`:no` のいずれか
  * `loglevel` - ロギングレベル（デフォルト: Logging.Info）

出力:

  * “リーダー”から対応する入力-出力方程式への辞書; 追加の射影が必要な場合は、`rand_proj_var` に対応する値になります
