```
BeliefMCTSSolver(mcts_solver, updater)
```

信念MCTSソルバーは、POMDPを信念空間上のMDPとしてモデル化することによって解決します。`updater`は、信念MDP生成モデルの一部として信念を更新するために使用されます。

例:

```
using ParticleFilters
using POMDPModels
using MCTS

pomdp = BabyPOMDP()
updater = SIRParticleFilter(pomdp, 1000)

solver = BeliefMCTSSolver(DPWSolver(), updater)
planner = solve(solver, pomdp)

simulate(HistoryRecorder(max_steps=10), pomdp, planner, updater)
```
