```julia
struct COPLS{dim, 𝒯, TL, TU, Tp} <: BifurcationKit.AbstractDirectLinearSolver
```

パラメータの凝縮に基づく線形ソルバー。

## フィールド

  * `cache::BifurcationKit.COPCACHE`

## コンストラクタ

  * `COPBLS()`
  * `COPBLS(coll::PeriodicOrbitOCollProblem; cache::COPCACHE, solver = nothing, J = nothing)`

## 関連

`solve_cop`を参照してください。
