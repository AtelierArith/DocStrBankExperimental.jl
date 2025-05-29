```
 get_mappings(data, freq; m = 3)
```

Returns the optimal mappings corresponding to the frequency 'freq'. Prints the position and strengh of peak at 'f' for control purposes. input :     - data : input categorical time series     - freq : the frequency where one wants the optimal mappings     - m : smoothing parameters (see 'spectral*envelope') returns :     - mappings : the mapping at the peak associated with the desired frequency. example:     # we have some data, plotting the spectral envelope, we see a peak at 0.33     m = get*mappings(data, 0.33)
