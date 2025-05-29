```
CompromiseProgramming(scalarizing)
```

`scalarizing`関数を使用して妥協プログラミングを実行します。現在実装されているスカラー化関数は次のとおりです。

  * `WeightedSum`
  * `Tchebysheff`
  * `AchievementScalarization`.

### 例

```julia-repl
julia> f, bounds, pf = Metaheuristics.TestProblems.ZDT1();

julia> res = optimize(f, bounds, NSGA2());

julia> w = [0.5, 0.5];

julia> sol = best_alternative(res, w, CompromiseProgramming(Tchebysheff()))
(f = [0.38493217206706115, 0.38037042164979956], g = [0.0], h = [0.0], x = [3.849e-01, 7.731e-06, …, 2.362e-07])

julia> sol = best_alternative(res, w, CompromiseProgramming(WeightedSum()))
(f = [0.2546059308425166, 0.4958366970021401], g = [0.0], h = [0.0], x = [2.546e-01, 2.929e-06, …, 2.224e-07])

julia> sol = best_alternative(res, w, CompromiseProgramming(AchievementScalarization()))
(f = [0.38493217206706115, 0.38037042164979956], g = [0.0], h = [0.0], x = [3.849e-01, 7.731e-06, …, 2.362e-07])

julia> idx = decisionmaking(res, w, CompromiseProgramming(Tchebysheff()))
3
```
