```
semimajor, eccentricity, inclination, phase = ap2ep(u::Complex,v::Complex)
semimajor, eccentricity, inclination, phase = ap2ep(amplitude_u,phase_u,amplitude_v,phase_v)
```

潮汐楕円のパラメータである半長軸（`semimajor`）、離心率、傾斜（度、東と最大流速の間の角度）、および位相（度）を、緯度および経度の速度の振幅と位相から取得します。速度は振幅と位相に関連しています：

u(t) = aᵤ cos(ω t - ϕᵤ) v(t) = aᵥ cos(ω t - ϕᵥ)

ここで、ωは潮汐の角周波数、tは時間です。

このコードは、Zhigang Xuによる技術報告書[Ellipse Parameters Conversion and Velocity Profile For Tidal Currents](https://www.researchgate.net/publication/312234150_Ellipse_Parameters_Conversion_and_Velocity_Profile_For_Tidal_Currents)に基づいています。

```
semiminor = semimajor * eccentricity
```

## 例

```julia
using PyPlot, PhysOcean
amplitude_u = 1.3
amplitude_v = 1.12
phase_u = 190
phase_v = 350

semimajor,  eccentricity, inclination, phase = ap2ep(amplitude_u,phase_u,amplitude_v,phase_v)
semiminor = semimajor * eccentricity

phase_ = 0:1:360
u = amplitude_u * cosd.(phase_ .- phase_u)
v = amplitude_v * cosd.(phase_ .- phase_v)

plot(u,v,"-",label="tidal ellipse")
plot([0,semimajor * cosd(inclination)],[0,semimajor * sind(inclination)],"-",label = "semi-major axis")
plot([0,semiminor * cosd(inclination+90)],[0,semiminor * sind(inclination+90)],"-",label = "semi-minor axis")
legend()
```
