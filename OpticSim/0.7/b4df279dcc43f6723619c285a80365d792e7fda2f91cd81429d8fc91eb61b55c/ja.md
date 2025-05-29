```
tracehitsMT(system::AbstractOpticalSystem{T}, raygenerator::OpticalRayGenerator{T}; printprog = true, test = false)
```

`system`を`raygenerator`によって生成された光線でトレースします。可能な限り多くのスレッドを使用します。オプションで、進行状況をREPLに印刷することができます。`test`が有効な場合、フレネル反射は無効になり、電力分布は正しくありません。

検出器にヒットした[`LensTrace`](@ref)sのリストを返します。これはすべてのスレッドから蓄積されたものです。
