```
struct LSRK54TimeStepper{T} <: AbstractTimeStepper{T}
```

4次の5段階2ストレージのルンゲ・クッタタイムステッパーで、`∂u/∂t = RHS(u, t)`を次のように時間ステッピングします：

```julia
S² = 0

for i = 1:5
  S² = Aᵢ * S² + dt * RHS(uⁿ, t₀ + Cᵢ * dt)
  uⁿ += Bᵢ * S²
end

uⁿ⁺¹ = uⁿ
```

ここで、`Aᵢ`、`Bᵢ`、および`Cᵢ`は、$i$-thステージのLSRKテーブルからの$A$、$B$、および$C$係数です。詳細については、[Carpenter-Kennedy-1994](@citet)を参照してください。

!!! info "使用法"
    `LSRK54TimeStepper`は[`RK4TimeStepper`](@ref)よりも*遅い*ですが、*メモリフットプリントが少ない*です；[`RK4TimeStepper`](@ref)の半分です。

    シミュレーションがパフォーマンスに制約されている場合は[`RK4TimeStepper`](@ref)を使用してください；シミュレーションがメモリに制約されている場合は`LSRK54TimeStepper`の使用を検討してください。

