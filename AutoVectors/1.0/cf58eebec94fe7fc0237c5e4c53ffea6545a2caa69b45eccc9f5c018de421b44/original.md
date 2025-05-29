```
fftav(f::AutoVector{Float64},delta)
```

For a real function f(x) defined by sampling on a uniform grid with spacing delta,  returns a tuple (F, freqsp, len), where F is the Fourier Transform as an AutoVector(ComplexF64),  freqsp is the frequency spacing of F, and len the length of the vector used in the FFT (to be used in ifftav). Implicitly, the function is assumed to be zero outside the range of the input. The normalizations are different from the usual discrete FT conventions, incorporating the spacing, and corresponding to a continuous integral. The FT is defined as

$F(k) = \frac{1}{\sqrt{2 \pi}} \int dx e^{-i k x} f(x)$
