```
pdepe(m, pdefunction, icfunction, bdfunction, xmesh, tspan ; params=SkeelBerzins.Params(), kwargs...)
```

1Dの楕円および放物型偏微分方程式を、[1]で説明されている空間離散化法を使用して解きます。この方法を使用するには、PDEの1つが放物型である必要があります。時間の離散化は、暗黙のオイラー法（内部法）によって行われるか、[DifferentialEquations.jl](https://github.com/SciML/DifferentialEquations.jl)パッケージのODE/DAEソルバーを使用して行われます。問題を解くためのさまざまな入力を定義する方法についての詳細は、次のセクションを参照してください：[問題定義](https://gregoirepourtier.github.io/SkeelBerzins.jl/dev/problem_definition/)および[ソルバー](https://gregoirepourtier.github.io/SkeelBerzins.jl/dev/solvers/)。

入力引数：

  * `m`: 問題の対称性を指すスカラー。`m=0`、`m=1`、または`m=2`のいずれかの値を取り、直交座標、円筒座標、または球座標をそれぞれ表します。
  * `pdefunction`: 関数。容量、フラックス、およびソース項を使用してPDEの定式化を定義します。
  * `icfunction`: 関数。解くべき問題の初期条件を定義します（`tstep!=Inf`の場合 - ODE/DAE問題からの初期条件、`tstep=Inf`の場合 - ニュートンソルバーに使用される初期値）。
  * `bdfunction`: 関数。問題の境界条件を定義します。
  * `xmesh`: ユーザーが解を得ることを意図している空間メッシュを表す1D配列。
  * `tspan`: 問題の時間間隔を表すタプル $(t_0, t_{end})$。

キーワード引数：

  * `params`: ソルバーからのキーワード引数を含む[`SkeelBerzins.Params`](@ref)構造体を定義します。
  * `kwargs`: [`SkeelBerzins.Params`](@ref)構造体を使用する代わりに、ユーザーはこの特定の構造体から直接フィールドをソルバーに渡すことができます。

選択したソルバー（:eulerまたは:DiffEq）に応じて、[`RecursiveArrayTools.DiffEqArray`](https://docs.sciml.ai/RecursiveArrayTools/stable/array_types/#RecursiveArrayTools.DiffEqArray)または[`SkeelBerzins.ProblemDefinition`](@ref)構造体を返します。得られた解は時間における線形補間法を含み、区間 $(t_0,t_{end})$ 内の任意の時間ステップで解を評価するために使用できます（`sol(t)`を使用してアクセス可能）。[`pdeval`](@ref)関数に似た空間補間が、コマンド `sol(x_eval,t,pb)`を使用して解オブジェクトで利用可能です。
