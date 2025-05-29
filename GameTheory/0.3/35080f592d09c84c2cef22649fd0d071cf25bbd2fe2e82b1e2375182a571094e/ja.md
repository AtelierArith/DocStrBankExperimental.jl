```
outerapproximation(rpd; nH=32, tol=1e-8, maxiter=500, check_pure_nash=true,
                   verbose=false, nskipprint=50,
                   plib=CDDLib.Library(),
                   lp_solver=GameTheory.highs_optimizer_silent)
```

Judd, Yeltekin, Conklin (2002) によって説明された外部ハイパープレーン近似を用いて、繰り返しゲームの均衡値の集合を近似します。

# 引数

  * `rpd::RepGame2` : 2人用の繰り返しゲーム。
  * `nH::Int` : 近似に使用されるサブグラディエントの数。
  * `tol::Float64` : 集合の差の許容範囲。
  * `maxiter::Int` : 最大反復回数。
  * `check_pure_nash`: 純粋ナッシュ均衡が存在するかどうかを確認するかどうか。
  * `verbose::Bool` : 反復と距離に関する更新を表示するかどうか。
  * `nskipprint::Int` : 情報を印刷する間の反復回数（verbose=trueを前提とする）。
  * `plib::Polyhedra.Library`: 幾何学的計算のために特定のパッケージを選択できるようにします。（詳細については [Polyhedra.jl](https://github.com/JuliaPolyhedra/Polyhedra.jl) のドキュメントを参照してください）。デフォルトでは、`CDDLib.Library()` を使用することを選択します。
  * `lp_solver` : 内部で使用される線形計画ソルバー。オプションが必要ない場合は `MathOptInterface.AbstractOptimizer` 型（例えば `HiGHS.Optimizer`）を渡すか、オプションを供給する関数（例えば `GameTheory.highs_optimizer_silent`）を渡します。

# 戻り値

  * `vertices::Matrix{Float64}` : 値集合の外部近似の頂点。
