```julia
DiscreteCallback(condition,affect!;
                 initialize = INITIALIZE_DEFAULT,
                 finalize = FINALIZE_DEFAULT,
                 save_positions=(true,true))
```

# 引数

  * `condition`: コールバックを使用すべき時を宣言する関数 `condition(u,t,integrator)` です。条件が `true` に評価されるとコールバックが開始されます。`integrator` に関する情報は [Integrator Interface](@ref integrator) ドキュメントを参照してください。

      * `affect!`: 現在の状態を変更することが許可されている関数 `affect!(integrator)` です。何ができるかについての詳細は [Integrator Interface](@ref integrator) マニュアルページを参照してください。
  * `save_positions`: `affect!` の前後に保存するかどうかのブールタプルです。この保存はイベントの直前と直後に、イベント時のみ発生し、`saveat`、`save_everystep` などのオプションには依存しません（つまり、`saveat=[1.0,2.0,3.0]` の場合でも、trueであれば `2.1` に保存ポイントを追加できます）。`u` の変更のような不連続な変化を正しく処理するためには、`save_positions=(true,true)` に設定する必要があります。
  * `initialize`: コールバック `c` の状態を初期化するために使用できる関数 `(c,u,t,integrator)` です。引数 `c` を変更する必要があり、戻り値は無視されます。
  * `finalize`: コールバック `c` の状態を最終化するために使用できる関数 `(c,u,t,integrator)` です。引数 `c` を変更する必要があり、戻り値は無視されます。
