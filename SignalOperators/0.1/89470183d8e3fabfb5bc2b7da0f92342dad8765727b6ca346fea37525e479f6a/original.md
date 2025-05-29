```
tosamplerate(x,fs;blocksize)
```

Change the sample rate of `x` to the given sample rate `fs`. Functionally defined signals (e.g. `signal(sin)`) are resampled exactly: the function is simply called more times to generate more samples. Data-based signals (`signal(rand(50,2))`) are resampled using filtering. In this case you can use the keyword arugment `blocksize` to change the analysis window used. See [`filtersignal`](@ref) for more details.
