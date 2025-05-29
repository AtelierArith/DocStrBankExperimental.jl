```
  Spec, BandEn = SpecEn(Sig)
```

Returns the spectral entropy estimate of the full spectrum (`Spec`)   and the within-band entropy (`BandEn`) estimated from the data sequence (`Sig`)   using the default  parameters:    N-point FFT = 2*len(`Sig`) + 1, normalised band edge frequencies = [0 1],   logarithm = base 2, normalisation = w.r.t # of spectrum/band frequency values.

```
  Spec, BandEn = SpecEn(Sig::AbstractArray{T,1} where T<:Real; N::Int=1 + (2*size(Sig,1)), Freqs::Tuple{Real,Real}=(0,1), Logx::Real=exp(1), Norm::Bool=true)
```

Returns the spectral entropy (`Spec`) and the within-band entropy (`BandEn`)   estimate for the data sequence (`Sig`) using the specified 'keyword' arguments:

# Arguments:

`N`     - Resolution of spectrum (N-point FFT), an integer > 1  

`Freqs` - Normalised band edge frequencies, a 2 element tuple with values 

```
        in range [0 1] where 1 corresponds to the Nyquist frequency (Fs/2).
        Note: When no band frequencies are entered, BandEn == SpecEn
```

`Logx`  - Logarithm base, a positive scalar (enter 0 for natural log) 

`Norm`  - Normalisation of `Spec` value:

```
        [false]  no normalisation.
        [true]   normalises w.r.t # of spectrum/band frequency values - default.
```

For more info, see the EntropyHub guide.

# See also `XSpecEn`, `fft`, `MSEn`,  `XMSEn`

# References:

```
  [1] G.E. Powell and I.C. Percival,
      "A spectral entropy method for distinguishing regular and 
      irregular motion of Hamiltonian systems." 
      Journal of Physics A: Mathematical and General 
      12.11 (1979): 2053.

  [2] Tsuyoshi Inouye, et al.,
      "Quantification of EEG irregularity by use of the entropy of 
      the power spectrum." 
      Electroencephalography and clinical neurophysiology 
      79.3 (1991): 204-210.
```
