```
execute!(
    sim::Simulation,
    solver;
    kwargs...
)
```

時間領域の動的シミュレーションモデルを解決します。

# 引数

  * `sim::Simulation` : 初期化されたシミュレーションオブジェクト
  * `solver` : 数値積分に使用されるソルバー。シミュレーションモデルのタイプに応じて正しく渡す必要があります。
  * `enable_progress_bar::Bool` : デフォルト: `true`。積分ルーチンの進行状況バーを有効にします。
  * 追加のソルバーキーワード引数を含めることができます。詳細については、`DifferentialEquations.jl` ドキュメントの [Common Solver Options](https://diffeq.sciml.ai/stable/basics/common_solver_opts/) を参照してください。
