```
solve(prob::NLODEProblem{F,PRTYPE,T,D,Z,CS},al::QSSAlgorithm{SolverType, OrderType},tspan::Tuple{Float64, Float64};detection::Val{M}=Val(3),saveat=Inf::Float64,abstol=1e-4::Float64,reltol=1e-3::Float64,maxErr=1.0::Float64,maxiters=Int(1e7)::Int) where{F,PRTYPE,T,D,Z,CS,SolverType,OrderType,M}
```

は、提供されたアルゴリズムに基づいて特定の積分器にディスパッチし、非線形ODE問題を積分器に送信します。

引数 prob と tspan を除いて、他のすべての引数はオプションであり、デフォルト値があります：

  * アルゴリズムのデフォルトは nmliqss2 であり、これは名前と順序を持つ複合型である QSSAlgorithm 型によって指定されます。これは、ソルバーとは独立して拡張できます。
  * detection 引数のデフォルトは 1 です。
  * saveat 引数のデフォルトは Inf です。これは、積分器が解を保存する時間ステップを指定します（未実装）。
  * abstol 引数のデフォルトは 1e-4 です。これは、積分器の絶対許容誤差を指定します。
  * reltol 引数のデフォルトは 1e-3 です。これは、積分器の相対許容誤差を指定します。
  * maxErr 引数のデフォルトは Inf です。これは、積分器によって許可される最大誤差を指定します。これは、変数が大きくなるときの量子の上限として使用されます。
  * maxiters 引数のデフォルトは 1e7 です。これは、積分器によって許可される最大ステップ数を指定します。ユーザーが最大ステップ数の制限を拡張したい場合、この引数を使用できます。

シミュレーションの後、解は Solution オブジェクトとして返されます。
