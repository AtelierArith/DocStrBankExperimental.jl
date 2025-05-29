```
test_solver(solver::Solver, problem::POMDP)
test_solver(solver::Solver, problem::MDP)
```

指定された問題を解決するためにソルバーを使用し、その後シミュレーションを実行します。

これは、ソルバーがどのように機能することが期待されているかを示すために設計されています。すべてのソルバーは、POMDPModelsパッケージのシンプルなモデルを使用して、この標準テストを完了できる必要があります。

これは解の最適性をテストするものではなく、ソルバーがPOMDPモデルと期待通りに相互作用するかどうかを確認するためのスモークテストに過ぎないことに注意してください。

YourSolverというソルバーでこれを実行するには、次のようにします。

```
using POMDPToolbox
using POMDPModels

solver = YourSolver(# パラメータで初期化 #)
test_solver(solver, BabyPOMDP())
```
