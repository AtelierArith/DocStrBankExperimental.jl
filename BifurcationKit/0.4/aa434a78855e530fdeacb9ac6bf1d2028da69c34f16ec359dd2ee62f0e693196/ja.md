```julia
mutable struct GMRESKrylovKit{T, Tl} <: BifurcationKit.AbstractIterativeLinearSolver
```

`KrylovKit.jl`の`linsolve`に基づいた線形ソルバーを作成します。これは、`(a₀ * I + a₁ * J) * x = rhs`を解くために使用できます。

## フィールド

  * `dim::Int64`: Krylov次元 デフォルト: KrylovDefaults.krylovdim[]
  * `atol::Any`: ソルバーの絶対許容誤差 デフォルト: KrylovDefaults.tol[]
  * `rtol::Any`: ソルバーの相対許容誤差 デフォルト: KrylovDefaults.tol[]
  * `maxiter::Int64`: 最大反復回数 デフォルト: KrylovDefaults.maxiter[]
  * `verbose::Int64`: 冗長性 ∈ {0,1,2} デフォルト: 0
  * `issymmetric::Bool`: 線形マップが対称であるかどうか、T<:Realの場合のみ意味があります デフォルト: false
  * `ishermitian::Bool`: 線形マップがエルミートであるかどうか デフォルト: false
  * `isposdef::Bool`: 線形マップが正定値であるかどうか デフォルト: false
  * `Pl::Any`: 左前処理器 デフォルト: nothing

!!! tip "異なる線形ソルバー"
    オプションを調整することで、CG、GMRESなどを選択できます... 詳細は[こちら](https://jutho.github.io/KrylovKit.jl/stable/man/linear/#KrylovKit.linsolve)を参照してください。

