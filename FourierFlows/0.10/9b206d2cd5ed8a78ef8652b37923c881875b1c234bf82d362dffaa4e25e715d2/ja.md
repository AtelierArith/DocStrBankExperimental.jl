```
struct RK4TimeStepper{T} <: AbstractTimeStepper{T}
```

4次のルンゲ・クッタタイムステッパーは、`∂u/∂t = RHS(u, t)` の時間ステッピングを行います：

```julia
uⁿ⁺¹ = uⁿ + dt/6 * (k₁ + 2 * k₂ + 2 * k₃ + k₄)
```

ここで、

```julia
k₁ = RHS(uⁿ, tⁿ)
k₂ = RHS(uⁿ + k₁ * dt/2, tⁿ + dt/2)
k₃ = RHS(uⁿ + k₂ * dt/2, tⁿ + dt/2)
k₄ = RHS(uⁿ + k₃ * dt, tⁿ + dt)
```

!!! info "使用法"
    シミュレーションがメモリに制限されている場合は、[`LSRK54TimeStepper`](@ref) に切り替えることを検討してください。[`LSRK54TimeStepper`](@ref) タイムステッパーは、`RK4TimeStepper` に比べて約半分のメモリフットプリントを持ち、パフォーマンスは約25%-30%のトレードオフがあります。

