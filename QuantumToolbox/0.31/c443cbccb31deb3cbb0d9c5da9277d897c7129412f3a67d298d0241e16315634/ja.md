```
eigsolve(A::QuantumObject; 
    v0::Union{Nothing,AbstractVector}=nothing, 
    sigma::Union{Nothing, Real}=nothing,
    eigvals::Int = 1,
    krylovdim::Int = max(20, 2*k+1),
    tol::Real = 1e-8,
    maxiter::Int = 200,
    solver::Union{Nothing, SciMLLinearSolveAlgorithm} = nothing,
    kwargs...)
```

行列 `A` の固有値と固有ベクトルをアーノルディ法を使用して解きます。

# 引数

  * `A::QuantumObject`: 固有値と固有ベクトルを解くための [`QuantumObject`](@ref) 。
  * `v0::Union{Nothing,AbstractVector}`: アーノルディ法の初期ベクトル。デフォルトはランダムベクトルです。
  * `sigma::Union{Nothing, Real}`: 固有値問題のシフト。デフォルトは `nothing` です。
  * `eigvals::Int`: 計算する固有値の数。デフォルトは `1` です。
  * `krylovdim::Int`: クライロフ部分空間の次元。デフォルトは `max(20, 2*k+1)` です。
  * `tol::Real`: アーノルディ法の許容誤差。デフォルトは `1e-8` です。
  * `maxiter::Int`: アーノルディ法の最大反復回数。デフォルトは `200` です。
  * `solver::Union{Nothing, SciMLLinearSolveAlgorithm}`: 線形ソルバーアルゴリズム。デフォルトは `nothing` です。
  * `kwargs`: ソルバーに渡される追加のキーワード引数。

# 注意事項

  * `solver` と追加の `kwargs` についての詳細は、[`LinearSolve.jl`](https://docs.sciml.ai/LinearSolve/stable/) を参照してください。

# 戻り値

  * `EigsolveResult`: 固有値、固有ベクトル、および固有値ソルバーに関する情報を含む構造体です。
