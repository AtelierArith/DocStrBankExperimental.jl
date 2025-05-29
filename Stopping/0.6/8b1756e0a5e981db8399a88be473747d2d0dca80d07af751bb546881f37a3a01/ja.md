```
`start!(stp::AbstractStopping; no_opt_check::Bool = false, kwargs...)`
```

Stoppingを更新し、停止する必要がある場合は`true`を返します。

目的は、最適化アルゴリズムを実行する必要があるかどうか、または最初から最適な解に到達しているかを知ることです。最適性とドメインエラーのチェックを回避するには、`no_opt_check`を`true`に設定します。

関数`start!`は、次の関数を順次呼び出します：`_domain_check(stp, x)`、`_optimality_check!(stp, x)`、`_null_test(stp, x)`、および`_user_check!(stp, x, true)`。

注意: - `start!`は`stp.meta.start_time`（以前に行われていない場合）、`stp.current_state.current_time`、および`stp.meta.optimality0`（`no_opt_check`がfalseの場合）を初期化します。           - キーワード引数は`_optimality_check!`呼び出しに渡されます。           - `StopRemoteControl`と互換性があります。
