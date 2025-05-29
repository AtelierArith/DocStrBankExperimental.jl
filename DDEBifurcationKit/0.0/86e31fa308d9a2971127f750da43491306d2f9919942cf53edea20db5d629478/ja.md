```julia
mutable struct DDE_DefaultEig{T, Tw, Tv} <: DDEBifurcationKit.AbstractDDEEigenSolver
```

DDEBifurcationKitのデフォルト固有値ソルバーは、juliaパッケージNonlinearEigenproblems.jlに基づいています。より正確には、固有値の計算には`NonlinearEigenproblems.iar_chebyshev`に依存しています。

## フィールド

  * `maxit::Int64`: デフォルト: 100
  * `which::Any`: デフォルト: real
  * `σ::Any`: デフォルト: 0.0
  * `γ::Any`: デフォルト: 1.0
  * `tol::Any`: デフォルト: 1.0e-10
  * `logger::Int64`: デフォルト: 0
  * `check_error_every::Int64`: デフォルト: 1
  * `v::Any`: デフォルト: nothing

## コンストラクタ

  * `DDE_DefaultEig(; kwargs...)` および `kwargs` は上記のフィールドです。
