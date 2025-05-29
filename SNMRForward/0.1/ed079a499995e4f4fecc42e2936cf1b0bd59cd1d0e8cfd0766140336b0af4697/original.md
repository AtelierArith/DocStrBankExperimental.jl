```
forward(F::MRSForward, m::Vector{<:Real})
```

Computes the complex response amplitude of a water content model for a given FID experiment setup, described by an `MRSForward` object. Returns response as a complex vector, in units of volts, one  element per pulse moment.

Parameters:

  * `F`: an `MRSForward` object containing the kernel for modelling
  * `m`: a vector containing water saturation at each depth in `F.zgrid`.
