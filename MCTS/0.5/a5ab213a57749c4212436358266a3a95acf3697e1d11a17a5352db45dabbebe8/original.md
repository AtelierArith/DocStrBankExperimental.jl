```
BeliefMCTSSolver(mcts_solver, updater)
```

The belief mcts solver solves POMDPs by modeling them as an MDP on the belief space. The `updater` is used to update the belief as part of the belief MDP generative model.

Example:

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
