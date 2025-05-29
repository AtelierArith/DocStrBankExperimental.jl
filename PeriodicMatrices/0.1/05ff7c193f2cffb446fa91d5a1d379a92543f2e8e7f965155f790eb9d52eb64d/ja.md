```
 psceig(A[, K = 1]; lifting = false, solver, reltol, abstol, dt) -> ce
```

連続時間周期行列の特性指数を計算します。

与えられた周期 `T` の正方連続時間周期行列 `A(t)` に対して、特性指数 `ce` は `log.(ev)/T` として計算されます。ここで、`ev` は特性乗数（すなわち、`A(t)` のモノドロミー行列の固有値）です。利用可能なオプションについては [`pseig(::PeriodicFunctionMatrix)`](@ref) を参照してください。`A` は [`PeriodicFunctionMatrix`](@ref)、[`HarmonicArray`](@ref)、[`PeriodicSymbolicMatrix`](@ref) または [`FourierFunctionMatrix`](@ref) として与えることができます。与えられた離散周期 `N` の正方離散時間周期行列 `A(t)` に対して、特性指数 `ce` は `ev.^-N` として計算されます。
