```
op = JopSft(dom,freqs,dt)
```

Polychromatic slow Fourier transforms for a specified list of frequencies. Tranform along the fast dimension of `dom::JetSpace{<:Real}`.

Notes:     - it is expected that the domain is 2D real of size [nt,ntrace]     - the range will be 2D complex of size [length(freqs),ntrace]     - regarding the factor of (2/n): the factor "1/n" is from the Fourier transform, and the "2" is from Hermittian symmetry.
