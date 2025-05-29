NashConvCallback(sol::AbstractCFRSolver, n=1)

  * `sol` :
  * `n`   : Frequency with which to query nash convergence e.g. `n=10` indicates checking exploitability every 10 CFR iterations

Usage:

```
using CounterfactualRegret
const CFR = CounterfactualRegret

game = CFR.Games.Kuhn()
sol = CFRSolver(game)
train!(sol, 10_000, cb=NashConvCallback(sol))
```
