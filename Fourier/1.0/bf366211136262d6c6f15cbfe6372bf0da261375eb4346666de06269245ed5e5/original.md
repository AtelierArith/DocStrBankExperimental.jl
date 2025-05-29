```
fftrange(n)
```

Computes a range that always matches FFT expectations.  I.e., for even N ranges matches the example n=4 => -2:1:1 and for odd N matches the example 5 => -2:1:2.

This can be understood as "the output range shall always contain zero, if there may be only one value for n÷2, it will be the negative one."

The range is always centered; frequency or sampling bins align to it with fftshift.  It can be fftshifted to be placed in post-FFT coordinates.
