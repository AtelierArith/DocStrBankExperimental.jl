```
generatesignals(fn, L)
```

Generates a signal of length 2ᴸ given the function symbol `fn`. Current accepted inputs  below are based on D. Donoho and I. Johnstone in "Adapting to Unknown Smoothness via Wavelet  Shrinkage" Preprint Stanford, January 93, p 27-28.  

  * `:blocks`
  * `:bumps`
  * `:heavisine`
  * `:doppler`
  * `:quadchirp`
  * `:mishmash`

The code for this function is adapted and translated based on MATLAB's Wavelet Toolbox's  `wnoise` function.

# Arguments

  * `fn::Symbol`: Type of function/signal to generate.
  * `L::Integer`: (Default = 7) Size of the signal to generate. Will return a signal of size 2ᴸ.

# Returns

`::Vector{Float64}`: Signal of length 2ᴸ.

# Examples

```repl
using WaveletsExt

generatesignals(:bumps, 8)
```
