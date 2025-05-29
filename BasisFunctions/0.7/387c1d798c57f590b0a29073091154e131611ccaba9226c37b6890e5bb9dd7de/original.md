A Fourier basis on the interval `[0,1]`. The basis functions are given by `exp(2 π i k)`, with `k` ranging from `-N` to `N` for Fourier series of odd length (`2N+1`) and from `-N+1` to `N` for even length. In the latter case, the highest frequency basis function corresponding to frequency `N` is a cosine.

The basis functions are ordered the way they are expected by a typical FFT implementation. The frequencies k are in the following order:

```
0 1 2 3 ... N -N -N+1 ... -2 -1,
```

for odd length and

```
0 1 2 3 ... N -N+1 ... -2 -1,
```

for even length.

The Fourier basis is orthonormal with respect to a continuous measure (for odd length Fourier bases only) and a discrete measure.
