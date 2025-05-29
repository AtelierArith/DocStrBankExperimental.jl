```julia
function brange(wl :: Int;
             DC :: Bool = false)
```

Return a range of bins for a real-FFT vector covering all Fourier discrete frequencies given window length `wl`.

If `DC` is false, the range is $1:(wl÷2)$ (integer division), otherwise it is $1:(wl÷2)+1$.

**See also**: [`f2b`](@ref), [`fres`](@ref), [`b2f`](@ref), [`fdf`](@ref).

**Examples**:

```julia
using FourierAnalysis
brange(0.5, 8) # return 1:4
```
