```
radiosity(m::UniformSky, sky::SkySectors, Idif::SVector{nw, Float64}) where nw
```

Calculate the radiosity of each section of `sky` on the horizontal plane given diffuse irradiance on the horizontal plane (`Idif` with `nw` wavebands) assuming a Uniform Sky model. See package documentation for details.
