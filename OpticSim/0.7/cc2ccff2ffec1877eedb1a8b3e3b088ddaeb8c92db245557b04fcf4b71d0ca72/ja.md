```
trace(system::AbstractOpticalSystem{T}, ray::OpticalRay{T}; trackrays = nothing, test = false)
```

`system`を`ray`でトレースします。`test`が有効な場合、フレネル反射は無効になり、電力分布は正しくなりません。`ray`が検出器に当たると、[`LensTrace`](@ref)を返し、それ以外の場合は`nothing`を返します。

`trackrays`には、`ray`がシステム内の表面と交差するたびに`LensTrace`オブジェクトを蓄積するために空のベクターを渡すことができます。
