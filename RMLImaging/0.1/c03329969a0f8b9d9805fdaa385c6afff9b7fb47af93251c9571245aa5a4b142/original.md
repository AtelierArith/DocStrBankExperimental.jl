```
SingleNFFT2D(nfft_fwd, nfft_adj, vnorm) <: FourierTransform2D
```

A Fourier Transform Operator of a single 2D Image using NFFT.

# Fields

  * `nfft_fwd`: NFFT operator for the forward transform
  * `nfft_adj`: NFFT operator for the adjoint transform
  * `Vkernel`: the factor (phase shift, pulse funciton, kernel, etc) to be multipled by the forward-transformed visibilities.
