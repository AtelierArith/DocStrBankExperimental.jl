```
radiosity(m::StandardSky, sky::SkySectors, Idif::SVector{nw, Float64})
```

Calculate the radiosity of each section of `sky` on the horizontal plane given diffuse irradiance on the horizontal plane (`Idif` with `nw` wavebands) assuming a Standard Sky model and for `nw` wavebands. See package documentation for details.
