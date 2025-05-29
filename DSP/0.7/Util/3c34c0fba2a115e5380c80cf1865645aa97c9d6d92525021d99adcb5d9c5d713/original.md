```
nextfastfft(n)
```

Return the closest product of 2, 3, 5, and 7 greater than or equal to `n`. FFTW contains optimized kernels for these sizes and computes Fourier transforms of input that is a product of these sizes faster than for input of other sizes.
