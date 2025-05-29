NashConvCallback(sol::AbstractCFRSolver, n=1)

  * `sol` :
  * `n`   : ナッシュ収束を照会する頻度。例えば、`n=10`は10回のCFRイテレーションごとに搾取可能性をチェックすることを示します。

使用法:

```
using CounterfactualRegret
const CFR = CounterfactualRegret

game = CFR.Games.Kuhn()
sol = CFRSolver(game)
train!(sol, 10_000, cb=NashConvCallback(sol))
```
