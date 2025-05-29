```
mcdm(fs, w, method)
```

指定された `method` を使用して、与えられた `fs` と重みベクトルに対して実行します。ここで、`fs` は非支配解の集合（集団）、`State` または意思決定行列である可能性があります。

また、`method` は `JMcDM` パッケージから選択できます。

サポートされている McDM メソッド:

  * `ArasMethod`
  * `CocosoMethod`
  * `CodasMethod`
  * `CoprasMethod`
  * `EdasMethod`
  * `ElectreMethod`
  * `GreyMethod`
  * `MabacMethod`
  * `MaircaMethod`
  * `MooraMethod`
  * `SawMethod`
  * `TopsisMethod` **（デフォルトメソッド）**
  * `VikorMethod`
  * `WPMMethod`
  * `WaspasMethod`
  * `MarcosMethod`
  * `ROVMethod`

### 例 1:

集団を使用して McDM を実行します。

```julia-repl
julia> using JMcDM

julia> _, _, population = Metaheuristics.TestProblems.ZDT1();

julia> dm = mcdm(population, [0.5, 0.5], TopsisMethod());

julia> population[dm.bestIndex]
(f = [0.5353535353535354, 0.2683214262030523], g = [0.0], h = [0.0], x = [5.354e-01, 0.000e+00, …, 0.000e+00])
```

### 例 2:

メタヒューリスティックの結果を使用して McDM を実行します。

```julia-repl
julia> using JMcDM

julia> f, bounds, _ = Metaheuristics.TestProblems.ZDT1();

julia> res = optimize(f, bounds, NSGA2());

julia> dm = mcdm(res, [0.5, 0.5], TopsisMethod());

julia> res.population[dm.bestIndex]
(f = [0.32301132058506055, 0.43208538139854685], g = [0.0], h = [0.0], x = [3.230e-01, 1.919e-04, …, 1.353e-04])
```
