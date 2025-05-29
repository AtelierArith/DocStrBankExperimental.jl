```julia
struct COPBLS{dim, 𝒯, TL, TU, Tp, Ts, Tj} <: BifurcationKit.AbstractBorderedLinearSolver
```

パラメータの凝縮に基づく境界付き線形ソルバー。構造体定義における `dim` は、位相条件を考慮した境界のサイズです。したがって、COPLSの場合は `dim = 1` であり、周期軌道の弧長連続性の場合は2つの制約（位相と弧長）があるため `dim = 2` です。

## フィールド

  * `cache::BifurcationKit.COPCACHE`: COPメソッドのためのキャッシュ。これはCOPCACHEのサブタイプです。
  * `solver::Any`: 線形ソルバー。デフォルトは `nothing` です。
  * `J::Any`: 境界付きヤコビ行列のためのキャッシュ。

## コンストラクタ

  * `COPBLS()`
  * `COPBLS(coll::PeriodicOrbitOCollProblem; N = 0, cache::COPCACHE, solver = nothing, J = nothing)`

## 関連

`solve_cop` を参照してください。
