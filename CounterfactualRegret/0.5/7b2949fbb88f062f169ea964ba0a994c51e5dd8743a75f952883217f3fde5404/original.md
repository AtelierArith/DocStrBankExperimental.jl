```
ExploitabilityCallback(sol::AbstractCFRSolver, n=1; p=1)
```

  * `sol` :
  * `n`   : Frequency with which to query exploitability e.g. `n=10` indicates checking exploitability every 10 CFR iterations
  * `p`   : Player whose exploitability is being measured

Usage:

```
using CounterfactualRegret
const CFR = CounterfactualRegret

game = CFR.Games.Kuhn()
sol = CFRSolver(game)
train!(sol, 10_000, cb=ExploitabilityCallback(sol))
```
