```
load_fits(fitsfile::String, T::Type{<:IntensityMap}))
```

This loads in a fits file that is more robust to the various imaging algorithms in the EHT, i.e. is works with clean, smili, eht-imaging. The function returns an `T<:IntensityMap`. By default if `T===IntensityMap` then we only return the Stokes I image. If `T<:IntensityMap{StokesParams}` then we return the full Stokes image.  
