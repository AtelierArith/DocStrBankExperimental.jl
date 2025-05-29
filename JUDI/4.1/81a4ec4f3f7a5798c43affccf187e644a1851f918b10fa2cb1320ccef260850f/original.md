```
time_resample(data, geometry_in, dt_new)
```

Resample the input data with sinc interpolation from the current time sampling (geometrty*in) to the new time sampling `dt*new`.

Parameters

  * `data`: Data to be reampled. If data is a matrix, resamples each column.
  * `geometry_in`: Geometry on which `data` is defined.
  * `dt_new`: New time sampling rate to interpolate onto.
