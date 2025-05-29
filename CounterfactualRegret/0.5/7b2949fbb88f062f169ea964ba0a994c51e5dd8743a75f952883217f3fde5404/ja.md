```
ExploitabilityCallback(sol::AbstractCFRSolver, n=1; p=1)
```

  * `sol` :
  * `n`   : 利用可能性を照会する頻度。例えば、`n=10`は10回のCFRイテレーションごとに利用可能性をチェックすることを示します。
  * `p`   : 利用可能性が測定されているプレイヤー

使用法:

```
using CounterfactualRegret
const CFR = CounterfactualRegret

game = CFR.Games.Kuhn()
sol = CFRSolver(game)
train!(sol, 10_000, cb=ExploitabilityCallback(sol))
```
