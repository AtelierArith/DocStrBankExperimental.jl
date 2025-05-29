```
wiener(input, signal, noise[, blurring])
```

Return the Wiener deconvolution of `input`, using the power spectrum of `signal` and `noise`.  If the `input` was blurred with a known blurring kernel, pass it as fourth argument, `blurring`.

All arguments must be arrays in the time/space domain and all of the same size, they will be converted into the frequency domain internally using the `fft` function.
