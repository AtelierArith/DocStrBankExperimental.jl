```
test_solver(solver::Solver, problem::POMDP)
test_solver(solver::Solver, problem::MDP)
```

Use the solver to solve the specified problem, then run a simulation.

This is designed to illustrate how solvers are expected to function. All solvers should be able to complete this standard test with the simple models in the POMDPModels package.

Note that this does NOT test the optimality of the solution, but is only a smoke test to see if the solver interacts with POMDP models as expected.

To run this with a solver called YourSolver, run

```
using POMDPToolbox
using POMDPModels

solver = YourSolver(# initialize with parameters #)
test_solver(solver, BabyPOMDP())
```
