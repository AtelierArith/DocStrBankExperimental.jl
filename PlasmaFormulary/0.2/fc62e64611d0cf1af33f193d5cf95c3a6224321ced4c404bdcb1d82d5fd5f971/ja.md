```
gyrofrequency(B::BField, p::ParticleLike; kw...)
gyrofrequency(B::BField, mass::Mass, q::Charge)
```

磁場中の荷電粒子の円運動のジャイロ周波数（またはサイクロトロン周波数）を計算します。ジャイロ周波数は、荷電粒子が磁場線の周りを回る際の角周波数です。

参考文献:

  * [PlasmaPy Documentation](https://docs.plasmapy.org/en/latest/api/plasmapy.formulary.frequencies.gyrofrequency.html)

# 例

```jldoctest; filter = r"(\^-1|⁻¹)"
julia> gyrofrequency(0.01u"T", :p)  # 陽子のジャイロ周波数
957883.3292211705 rad s⁻¹

julia> uconvert(u"Hz", gyrofrequency(0.1u"T", :e), Periodic())  # 電子のジャイロ周波数を周波数として
2.799248987233304e9 Hz

julia> gyrofrequency(250u"Gauss", "Fe"; z=13)  # Fe2+ イオンのジャイロ周波数
560682.3520611608 rad s⁻¹
```
