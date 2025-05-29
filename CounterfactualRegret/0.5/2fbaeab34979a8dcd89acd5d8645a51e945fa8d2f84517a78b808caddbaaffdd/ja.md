複数のコールバックを連結する

使用法:

```
using CounterfactualRegret
const CFR = CounterfactualRegret


game = CFR.Games.Kuhn()
sol = CFRSolver(game)
exp_cb = ExploitabilityCallback(sol)
test_cb = Throttle(() -> println("test"), 100)
train!(sol, 10_000, cb=CFR.CallbackChain(exp_cb, test_cb))
```
