```julia
struct Params
```

ソルバー [`pdepe`](@ref) のためのすべてのキーワード引数を含む構造体。

  * `solver::Symbol`: 時間離散化の選択。内部の暗黙のオイラー法を使用する場合は `:euler`、または [DifferentialEquations.jl](https://github.com/SciML/DifferentialEquations.jl) パッケージを使用する場合は `:DiffEq`。
  * `tstep::Union{Float64, Vector{Float64}}`: 暗黙のオイラー法を使用する際の時間ステップを定義します（`Float64` または `Vector` を渡します）。`tstep=Inf` に設定すると、問題の定常版を解きます。
  * `hist::Bool`: フラグ。解とともに、ニュートンソルバーからの履歴を持つ1次元配列のリストを返します。
  * `sparsity::Symbol`: ヤコビアンを格納するために使用する行列のタイプ（`:sparseArrays`, `:banded`）の選択。
  * `linsolve::Union{Nothing, LinearSolve.SciMLLinearSolveAlgorithm}`: ニュートン法におけるLSEのソルバーの選択。詳細は [`LinearSolve.jl`](https://docs.sciml.ai/LinearSolve/stable/solvers/solvers/) を参照。
  * `maxit::Int64`: ニュートンソルバーの最大反復回数。
  * `tol::Float64`: ニュートン法で使用される許容誤差。$||\; u_{i+1} - u_{i} \;||_2 <$ `tol` の場合に解を返します。
  * `data::Bool`: PDE問題のデータを返します。
  * `nb_design_var::Int64`: PDE制約最適化のための設計変数の数。
