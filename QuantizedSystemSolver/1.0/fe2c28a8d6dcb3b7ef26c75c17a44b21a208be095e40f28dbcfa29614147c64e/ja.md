```
solve(prob::NLODEProblem{F,PRTYPE,T,D,Z,CS},al::QSSAlgorithm{SolverType, OrderType};detection::Val{M}=Val(3),saveat=Inf::Float64,abstol=1e-4::Float64,reltol=1e-3::Float64,maxErr=1.0::Float64,maxiters=Int(1e7)::Int,verbose=false::Bool) where{F,PRTYPE,T,D,Z,CS,SolverType,OrderType,M}
```

特定の積分器に基づいてディスパッチし、非線形ODE問題を積分器に送信します。

# 引数

  * `prob::NLODEProblem{F,PRTYPE,T,D,Z,CS}`: 解くべき非線形ODE問題。
  * `al::QSSAlgorithm{SolverType, OrderType}`: 問題を解くために使用するQSSアルゴリズム。
  * `detection::Val{M}`: どの検出メカニズムを使用するかを示す型パラメータ。
  * `saveat::Float64`: 解を保存する時間間隔（デフォルト: `Inf`）。
  * `abstol::Float64`: ソルバーの絶対許容誤差（デフォルト: `1e-4`）。
  * `reltol::Float64`: ソルバーの相対許容誤差（デフォルト: `1e-3`）。
  * `maxErr::Float64`: 許容される最大誤差（デフォルト: `Inf`）。
  * `maxiters::Int`: 最大反復回数（デフォルト: `Int(1e7)`）。
