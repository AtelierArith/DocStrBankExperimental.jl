```
(x,y,z0,z90) = phscen(cut, fghz=11.80285268; min_dropoff=-10)
```

Estimate phase center for a cut file or `Cut` object using NSI least-squares algorithm.

The four outputs are estimates of the location of the phase center relative to the origin used in recording the data in the cut.  If `fghz` is passed in as  an argument, the values will be expressed in units of inches.  Otherwise the  lengths will be normalized to wavelengths. Note that `z0` and `z90` are the  phi = 0ᵒ and phi = 90ᵒ plane estimates of the phase center location.   In determining the phase center locations, only field values with magnitudes in dB greater than `min_dropoff` relative to the peak field are considered.
