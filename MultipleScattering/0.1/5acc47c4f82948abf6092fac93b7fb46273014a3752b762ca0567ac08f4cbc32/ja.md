```
internal_field(x::AbstractVector, p::Particle{Dim,Acoustic{T,Dim}},  source::RegularSource, ω::T, scattering_coefficients::AbstractVector{Complex{T}})
```

音響媒質内の音響粒子の内部場。球体および円筒に対しては結果が正確であり、それ以外のすべてに対しては滑らかな場を仮定した近似です。
