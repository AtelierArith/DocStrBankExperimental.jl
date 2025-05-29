```julia
struct ODESolution{T, N, uType, uType2, DType, tType, rateType, discType, P, A, IType, S, AC<:Union{Nothing, Vector{Int64}}, R, O, V} <: SciMLBase.AbstractODESolution{T, N, uType}
```

常微分方程の解を表す構造体で、ODEProblemによって定義されます。

## DESolution インターフェース

`DESolution` タイプとの相互作用に関する詳細は、DifferentialEquations.jl ドキュメントのソリューション処理ページを参照してください。

https://docs.sciml.ai/DiffEqDocs/stable/basics/solution/

## フィールド

  * `u`: ODE解の表現。解の配列として与えられ、`u[i]` は時刻 `t[i]` における解に対応します。ほとんどの場合、`sol.u` に直接アクセスするのではなく、DifferentialEquations.jl ドキュメントのソリューション処理ページで説明されている配列インターフェースを使用することが推奨されます。
  * `t`: ODE解の保存された値に対応する時間点。
  * `prob`: 解かれた元のODEProblem。
  * `alg`: ソルバーによって使用されるアルゴリズムのタイプ。
  * `stats`: ソルバーの統計情報、必要な関数評価の数、計算されたヤコビ行列の数など。
  * `retcode`: ソルバーからの戻りコード。ソルバーが成功裏に解決したか、ユーザー定義のコールバックによって早期に終了したか、エラーによって終了したかを判断するために使用されます。詳細については、[戻りコードのドキュメント](https://docs.sciml.ai/SciMLBase/stable/interfaces/Solutions/#retcodes)を参照してください。
