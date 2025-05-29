```
gaussian_beam(res::Healpix.Resolution, angle_std_rad; normalization = 1.0) where {T,O <: Healpix.Order}
gaussian_beam(nside::Integer, angle_std_rad; normalization = 1.0) where {T,O <: Healpix.Order}
```

Save a map of a circual Gaussian beam in `beam_map`. The width of the beam is provided through the parameter `angle_std_rad`, which is expressed in radians. If you want to specify the FWHM instead, use `fwhm2std` like in the following example:

```julia
# Assume 2.5° of FWHM
beam_map = gaussian_beam(1024, 2.5 |> fwhm2std)
```

See also `gaussian_beam!`.
