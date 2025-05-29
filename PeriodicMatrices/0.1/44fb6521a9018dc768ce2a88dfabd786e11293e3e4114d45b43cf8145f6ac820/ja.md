```
 psceigsm(A::PeriodicSymbolicMatrix[, K = 1]; lifting = false, solver, reltol, abstol, dt) -> ce
```

周期的な記号行列の特性指数を計算します。

与えられた正方形の連続時間周期関数行列 `A(t)` の周期 `T` に対して、特性指数 `ce` は `log.(ev)/T` として計算されます。ここで、`ev` は特性乗数（すなわち、`A(t)` のモノドロミー行列の固有値）です。利用可能なオプションについては [`pseig(::PeriodicFunctionMatrix)`](@ref) を参照してください。
