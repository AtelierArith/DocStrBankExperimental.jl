```
SimulatorForwardProblem(f, p0::AbstractVector, observables::SimulatorObservable...)
```

呼び出し可能な関数 `f(x)` と観測量から `SimulatorForwardProblem` を構築します。基本問題は `SimpleForwardProblem` で、`f(x)` をラップし、`p0` を `x` のデフォルトパラメータ/入力値として使用します。
