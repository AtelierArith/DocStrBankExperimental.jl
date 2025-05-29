```
smooth(self::RheoTimeData, τ::Real; pad::String="reflect")
```

Smooth data using a Gaussian Kernel to time scale `τ` (approximately half power).

Smooths both `σ` and `ϵ`. Sampling frequency must be constant as it is based on FFT convolution. Essentially a low pass filter with frequencies of 1/τ being cut to approximately half power. For other pad types available see ImageFiltering documentation. As of doc writing, pad options are: `"replicate"` (repeat edge values to infinity), `"circular"` (image edges "wrap around"), `"symmetric"` (the image reflects relative to a position between pixels), `"reflect"` (the image reflects relative to the edge itself).
