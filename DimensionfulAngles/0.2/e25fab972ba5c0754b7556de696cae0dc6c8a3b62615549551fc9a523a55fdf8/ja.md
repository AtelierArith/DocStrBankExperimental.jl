```
Periodic()
```

時間的または空間的な周期、周波数、[角周波数](https://en.wikipedia.org/wiki/Angular_frequency)、および角周期間の変換の同等性。

これらの量は $f = ω/2π = 1/T = 1/(2πT̅)$ によって関連付けられます。ここで、

  * $$
    f
    $$

    は（時間的）周波数、
  * $$
    ω
    $$

    は（時間的）角周波数、
  * $$
    T
    $$

    は（時間的）周期、
  * $$
    T̅
    $$

    は（時間的）角周期、

および $ν = k/2π = 1/λ = 1/(2πλ̄)$ であり、ここで

  * $$
    ν
    $$

    は（空間的）周波数（線形波数）、
  * $$
    k
    $$

    は（空間的）角周波数（角波数）、
  * $$
    λ
    $$

    は（空間的）周期（線形波長）、および
  * $$
    λ̄
    $$

    は（空間的）角周期（角波長）です。

[`DimensionfulAngles.Dispersion`](@ref) も参照してください。

# 例

```jldoctest; filter = r"(\d*).(\d{1,10})\d+" => s"\1.\2"
julia> using Unitful

julia> using DimensionfulAngles

julia> uconvert(u"s", 10u"Hz", Periodic())
0.1 s

julia> uconvert(u"radᵃ/s", 1u"Hz", Periodic())
6.283185307179586 rad s⁻¹
```
