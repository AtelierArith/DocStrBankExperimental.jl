```
OptimizationProfiler{S, opType, optsType}
```

逐次再最適化を使用して尤度関数をプロファイリングするプロファイラメソッドです。

### フィールド

  * `stepper::S`: 次のプロファイルポイントを計算するために使用されるアルゴリズム。
  * `optimizer::opType`: 最適化プロセスに使用される最適化器。
  * `optimizer_opts::optsType`: 最適化器のオプション。デフォルトは `NamedTuple()` です。

### 例

```julia
using Optimization
profiler = OptimizationProfiler(; optimizer = Optimization.LBFGS(), optimizer_opts = (reltol=1e-4,), stepper = FixedStep())
```
