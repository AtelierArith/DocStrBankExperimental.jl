```julia
DiscreteCallback(condition, affect!;
    initialize = INITIALIZE_DEFAULT,
    finalize = FINALIZE_DEFAULT,
    save_positions = (true, true),
    initializealg = nothing)
```

# 引数

  * `condition`: コールバックを使用すべき時を宣言する関数 `condition(u,t,integrator)` です。条件が `true` に評価されるとコールバックが開始されます。`integrator` に関する情報は [Integrator Interface](@ref integrator) ドキュメントを参照してください。

      * `affect!`: 現在の状態を変更することが許可されている関数 `affect!(integrator)` です。何ができるかについての詳細は [Integrator Interface](@ref integrator) マニュアルページを参照してください。
  * `save_positions`: `affect!` の前後に保存するかどうかのブールタプルです。この保存はイベントの直前と直後に、イベント時のみ発生し、`saveat`、`save_everystep` などのオプションには依存しません（つまり、`saveat=[1.0,2.0,3.0]` の場合でも、`true` であれば `2.1` に保存ポイントを追加できます）。`u` の変更のような不連続な変化が正しく処理されるためには、`save_positions=(true,true)` に設定する必要があります。
  * `initialize`: コールバック `c` の状態を初期化するために使用できる関数 `(c,u,t,integrator)` です。引数 `c` を変更する必要があり、戻り値は無視されます。
  * `finalize`: コールバック `c` の状態を最終化するために使用できる関数 `(c,u,t,integrator)` です。引数 `c` を変更する必要があり、戻り値は無視されます。
  * `initializealg = nothing`: DAE の文脈において、効果の後に初期化を実行するために使用されるアルゴリズムです。デフォルトの `nothing` は `solve` で提供される初期化アルゴリズムに委ねます。

!!! warn
    DAE でコールバックを使用する効果は注意して行う必要があります。なぜなら、解 `u` は次のステップを取る前に代数的制約を満たす必要があるからです。このため、コールバックを実行した後に一貫した初期化計算を実行する必要があります。選択した初期化アルゴリズムが `BrownBasicInit()`（`solve` のデフォルト）である場合、初期化は条件を満たすように代数変数を変更します。したがって、`x` が代数変数であり、コールバックが `x+=1` を実行すると、初期化は制約を満たすために変更を「戻す」可能性があります。この動作は `initializealg = CheckInit()` に設定することで除去できます。これは単に状態 `u` が一貫していることを確認しますが、`affect!` の結果が制約を満たすことを要求します（さもなければエラーになります）。`NoInit()` を使用することは推奨されません。なぜなら、それは初期化後に不安定なステップを引き起こすからです。この警告は非 DAE ODE に対して無視できます。

