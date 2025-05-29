```
Dispersion(; dispersion=nothing, dispersion_inverse=nothing)
```

特定の[分散関係](https://en.wikipedia.org/wiki/Dispersion_relation)を使用して、時間周波数と空間周波数の間で変換するための同等性。

これは、提供された分散関係に基づいて空間量と時間量の間で変換するためのPeriodic()同等性を拡張します。

関連情報として[`DimensionfulAngles.Periodic`](@ref)を参照してください。

# 例

```jldoctest; filter = r"(\d*).(\d{1,10})\d+" => s"\1.\2"
julia> using DimensionfulAngles, Unitful

julia> g = Unitful.gn  # 重力加速度
9.80665 m s⁻²

julia> deepwater = Dispersion(
        dispersion = (k -> √(g*k*θ₀)), dispersion_inverse = (ω -> ω^2/(g*θ₀))
       );

julia> uconvert(u"radᵃ/mm", 1.0u"Hz", deepwater)
0.004025678249387654 rad mm⁻¹
```

一部の分散関係には、表現可能な逆がありません。そのような場合、`Roots.jl`を使用することが有益かもしれません。例えば、深水近似なしで線形の[水波分散](https://en.wikipedia.org/wiki/Dispersion_(water_waves))を使用する方法は次のとおりです。

```jldoctest; filter = r"(\d*).(\d{1,10})\d+" => s"\1.\2"
julia> using DimensionfulAngles, Unitful, Roots

julia> g = Unitful.gn  # 重力加速度
9.80665 m s⁻²

julia> k0 = (2π)u"radᵃ/m"  # 初期推定: 1m 波長
6.283185307179586 rad m⁻¹

julia> h = 0.5u"m"  # 水深
0.5 m

julia> waterwaves = Dispersion(
        dispersion = (k -> √(k*θ₀*g*tanh(k*h/θ₀))),
        dispersion_inverse = (ω -> solve(ZeroProblem(k -> k - ω^2/(g*tanh(k*h/θ₀))/θ₀, k0)))
       );

julia> uconvert(u"Hz", 0.004025678249387654u"radᵃ/mm", waterwaves)
0.9823052153509486 Hz

julia> h = (Inf)u"m"  # 水深
Inf m

julia> waterwaves = Dispersion(
        dispersion = ( k -> √(k*θ₀*g*tanh(k*h/θ₀)) ),
        dispersion_inverse = (ω -> solve(ZeroProblem(k -> k - ω^2/(g*tanh(k*h/θ₀))/θ₀, k0)))
       );

julia> uconvert(u"Hz", 0.004025678249387654u"radᵃ/mm", waterwaves) ≈ 1u"Hz"
true
```
