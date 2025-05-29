```
tracehits(system::AbstractOpticalSystem{T}, raygenerator::OpticalRayGenerator{T}; printprog = true, test = false)
```

`system`を`raygenerator`によって生成された光線で単一スレッドでトレースします。オプションで、進行状況をREPLに印刷することができます。`test`が有効な場合、フレネル反射は無効になり、電力分布は正しくありません。

検出器に当たった[`LensTrace`](@ref)のリストを返します。
