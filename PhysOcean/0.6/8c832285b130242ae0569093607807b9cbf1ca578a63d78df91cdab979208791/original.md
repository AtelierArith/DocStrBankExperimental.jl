```
semimajor, eccentricity, inclination, phase = ap2ep(u::Complex,v::Complex)
semimajor, eccentricity, inclination, phase = ap2ep(amplitude_u,phase_u,amplitude_v,phase_v)
```

Return the tidal elipise parameter semi-major axis (`semimajor`), `eccentricity`, inclination (degrees, angle between east and the maximum current) and phase (degrees) from the amplitude and phase of the meridional and zonal velocity. The velocities are related to the amplitude and phase by:

u(t) = aᵤ cos(ω t - ϕᵤ) v(t) = aᵥ cos(ω t - ϕᵥ)

where ω is the tidal angular frequency and t the time.

The code is based on the technical report [Ellipse Parameters Conversion and Velocity Profile For Tidal Currents](https://www.researchgate.net/publication/312234150_Ellipse_Parameters_Conversion_and_Velocity_Profile_For_Tidal_Currents) from Zhigang Xu.

```
semiminor = semimajor * eccentricity
```

## Example

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
