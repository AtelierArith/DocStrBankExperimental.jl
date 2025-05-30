```julia
struct RODESolution{T, N, uType, uType2, DType, tType, randType, P, A, IType, S, AC<:Union{Nothing, Vector{Int64}}} <: SciMLBase.AbstractRODESolution{T, N, uType}
```

確率微分方程式（SDEProblem）によって定義された解の表現、またはランダム常微分方程式（RODEProblem）によって定義された解の表現。

## DESolution インターフェース

`DESolution` タイプとの相互作用に関する詳細は、DifferentialEquations.jl ドキュメントのソリューション処理ページを参照してください。

https://docs.sciml.ai/DiffEqDocs/stable/basics/solution/

## フィールド

  * `u`: SDE または RODE 解の表現。解の配列として与えられ、`u[i]` は時刻 `t[i]` における解に対応します。ほとんどの場合、`sol.u` に直接アクセスすることは推奨されず、代わりに DifferentialEquations.jl ドキュメントのソリューション処理ページで説明されている配列インターフェースを使用することが推奨されます。
  * `t`: ODE 解の保存された値に対応する時間点。
  * `W`: 解から保存されたノイズプロセスの表現。DifferentialEquations.jl の[ノイズプロセスページ](https://docs.sciml.ai/DiffEqDocs/stable/features/noise_process/)を参照してください。このノイズは、ソルバーで `save_noise=true` の場合にのみ完全に保存されます。
  * `prob`: 解かれた元の SDEProblem/RODEProblem。
  * `alg`: ソルバーによって使用されるアルゴリズムのタイプ。
  * `stats`: ソルバーの統計情報、例えば必要な関数評価の数、計算されたヤコビアンの数など。
  * `retcode`: ソルバーからの戻りコード。ソルバーが成功裏に解決したか、ユーザー定義のコールバックによって早期に終了したか、またはエラーによって終了したかを判断するために使用されます。詳細については、[戻りコードのドキュメント](https://docs.sciml.ai/SciMLBase/stable/interfaces/Solutions/#retcodes)を参照してください。
