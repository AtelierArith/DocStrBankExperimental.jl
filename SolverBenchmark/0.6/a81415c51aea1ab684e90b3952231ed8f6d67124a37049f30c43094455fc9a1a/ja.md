```
solve_problems(solver, solver_name, problems; kwargs...)
```

ソルバーを一連の問題に適用します。

#### 引数

  * `solver`: ソルバーの関数名;
  * `solver_name`: ソルバーの名前;
  * `problems`: ソルバーに渡す問題のセットで、`AbstractNLPModel`のイテラブルとして。ジェネレーター式を使用することを推奨します（CUTEst問題には必要です）。

#### キーワード引数

  * `solver_logger::AbstractLogger`: ソルバー呼び出しをラップするロガー（デフォルト: `NullLogger`）;
  * `reset_problem::Bool`: 解決前に問題のカウンターをリセットするかどうか（デフォルト: `true`）;
  * `skipif::Function`: 問題に適用され、スキップするかどうかを返す関数（デフォルト: `x->false`）;
  * `colstats::Vector{Symbol}`: ベンチマーク中にロガーが出力する要約統計（デフォルト: `[:name, :nvar, :ncon, :status, :elapsed_time, :objective, :dual_feas, :primal_feas]`）;
  * `info_hdr_override::Dict{Symbol,String}`: 要約統計のヘッダーオーバーライド（デフォルト: デフォルトヘッダーを使用）;
  * `prune`: 最終統計にスキップされた問題を含めない（デフォルト: `true`）;
  * ソルバーに渡す他の任意のキーワード引数。

#### 戻り値

  * 各行が問題を表す`DataFrame`で、`prune`がtrueの場合はスキップされたものを除きます。
