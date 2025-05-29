```
(s::Spectrum)(ω::Real,usteady,ps=[];wtol=0)
```

From an instance of [`Spectrum`](@ref) `s`, actually compute the spectral power density at the frequency `ω`. Numerically solves the equation `x=inv(A)*b` where `x` is the vector containing the Fourier transformed correlation function, i.e. the spectrum is given by `real(x[1])`. `A` and `b` are a matrix and a vector, respectively, describing the linear system of equations that needs to be solved to obtain the spectrum. The tolerance `wtol=0` specifies in which range the frequency should be treated as zero, i.e. whenever `abs(ω) <= wtol` the term proportional to `1/(im*ω)` is neglected to avoid divergences.
