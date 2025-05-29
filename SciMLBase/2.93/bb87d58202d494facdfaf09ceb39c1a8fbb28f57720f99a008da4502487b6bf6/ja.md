```julia
ContinuousCallback(condition, affect!, affect_neg!;
    initialize = INITIALIZE_DEFAULT,
    finalize = FINALIZE_DEFAULT,
    idxs = nothing,
    rootfind = LeftRootFind,
    save_positions = (true, true),
    interp_points = 10,
    abstol = 10eps(), reltol = 0, repeat_nudge = 1 // 100,
    initializealg = nothing)
```

```julia
ContinuousCallback(condition, affect!;
    initialize = INITIALIZE_DEFAULT,
    finalize = FINALIZE_DEFAULT,
    idxs = nothing,
    rootfind = LeftRootFind,
    save_positions = (true, true),
    affect_neg! = affect!,
    interp_points = 10,
    abstol = 10eps(), reltol = 0, repeat_nudge = 1 // 100,
    initializealg = nothing)
```

単一のコールバックを含み、その `condition` は連続関数です。このコールバックは、この関数が 0 に評価されるとトリガーされます。

# 引数

  * `condition`: コールバックを使用するタイミングを宣言する関数 `condition(u,t,integrator)` です。条件が時間間隔内で `0` に達するとコールバックが開始されます。`integrator` に関する情報は [Integrator Interface](@ref integrator) ドキュメントを参照してください。
  * `affect!`: 現在の状態を変更することが許可されている関数 `affect!(integrator)` です。`affect_neg!` 関数を渡さない場合、`condition` が `0`（根で）と見なされ、交差が上交差（負から正）または下交差（正から負）のいずれかであるときに呼び出されます。上交差のときのみ呼び出されるべき場合は、`nothing` を `affect_neg!` 引数として明示的に渡す必要があります。詳細については、[Integrator Interface](@ref integrator) マニュアルページを参照してください。`u` の変更はこの関数内で安全です。
  * `affect_neg!=affect!`: 現在の状態を変更することが許可されている関数 `affect_neg!(integrator)` です。これは、`condition` が `0`（根で）と見なされ、交差が下交差（正から負）であるときに呼び出されます。詳細については、[Integrator Interface](@ref integrator) マニュアルページを参照してください。`u` の変更はこの関数内で安全です。
  * `rootfind=LeftRootFind`: イベントの位置を見つけるためのルート探索の種類を指定するフラグです。これが `LeftRootFind` に設定されている場合、解は `condition==0` のポイントに戻され、解が正確でない場合はルートの左限界が使用されます。`RightRootFind` に設定されている場合、解はルートの右限界に設定されます。それ以外の場合、システムと `affect!` は `t+dt` で発生します。これらの列挙型はエクスポートされていないため、`SciMLBase.LeftRootFind`、`SciMLBase.RightRootFind`、または `SciMLBase.NoRootFind` として参照する必要があります。
  * `interp_points=10`: 条件をチェックするための補間ポイントの数です。条件は、任意の補間ポイント/エンドポイントが異なる符号を持つかどうかをチェックすることで見つけられます。`interp_points=0` の場合、条件の符号が `t` で `t+dt` の符号と異なる場合にのみ条件が認識されます。この動作は解が振動する場合には堅牢ではないため、いくつかの補間ポイントを使用することをお勧めします（計算は安価です！）。時間間隔内の `0`。
  * `save_positions=(true,true)`: `affect!` の前後に保存するかどうかのブールタプルです。この保存はイベントの直前と直後にのみ発生し、イベント時刻でのみ行われ、`saveat`、`save_everystep` などのオプションには依存しません（つまり、`saveat=[1.0,2.0,3.0]` の場合、真であれば `2.1` で保存ポイントを追加できます）。`u` の不連続な変更が正しく処理されるためには（エラーなしで）、`save_positions=(true,true)` を設定する必要があります。
  * `idxs=nothing`: 条件に補間されるコンポーネントです。デフォルトは `nothing` で、これは `u` がすべてのコンポーネントであることを意味します。
  * `initialize`: コールバック `c` の状態を初期化するために使用できる関数 `(c,u,t,integrator)` です。引数 `c` を変更する必要があり、戻り値は無視されます。
  * `finalize`: コールバック `c` の状態を最終化するために使用できる関数 `(c,u,t,integrator)` です。引数 `c` を変更することができ、戻り値は無視されます。
  * `abstol=1e-14` & `reltol=0`: ルートファインダーのためのゼロからの許容誤差を指定するために使用されます。開始条件がゼロからの許容誤差未満の場合、ルートは検出されません。これは、ルートファインディングイベントの直後に繰り返しイベントが発生するのを防ぐためです。
  * `repeat_nudge = 1//100`: 以前に見つかったゼロの後の次のテストポイントを設定するために使用されます。デフォルトは 1//100 で、コールバックの後、次の符号チェックは t + dt*1//100 で行われ、t ではなく繰り返しを避けます。
  * `initializealg = nothing`: DAE の文脈では、効果の後に初期化を実行するために使用されるアルゴリズムです。デフォルトの `nothing` は、`solve` で提供される初期化アルゴリズムに委ねます。

!!! warn
    DAE でコールバックを使用する効果は注意が必要です。なぜなら、解 `u` は次のステップを取る前に代数的制約を満たす必要があるからです。このため、コールバックを実行した後に一貫した初期化計算を実行する必要があります。選択した初期化アルゴリズムが `BrownBasicInit()`（`solve` のデフォルト）である場合、初期化は条件を満たすように代数変数を変更します。したがって、`x` が代数変数であり、コールバックが `x+=1` を実行すると、初期化は制約を満たすために変更を「戻す」可能性があります。この動作は、状態 `u` が一貫していることを単に確認する `initializealg = CheckInit()` を設定することで取り除くことができますが、`affect!` の結果が制約を満たす必要があります（さもなければエラーが発生します）。`NoInit()` を使用することは推奨されません。なぜなら、それは初期化後の不安定なステップにつながるからです。この警告は非 DAE ODE に対して無視できます。

