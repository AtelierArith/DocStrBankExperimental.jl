```
remez(numtaps::Integer, band_defs;
      Hz::Real=1.0,
      neg::Bool=false,
      maxiter::Integer=25,
      grid_density::Integer=16)
```

Calculate the minimax optimal filter using the Remez exchange algorithm [^McClellan1973a] [^McClellan1973b].

This is the simplified API that accepts just 2 required arguments (numtaps, band_defs). For a scipy compatible version see the 3 arguments version (numtaps, bands, desired). 

Calculate the filter-coefficients for the finite impulse response (FIR) filter whose transfer function minimizes the maximum error between the desired gain and the realized gain in the specified frequency bands using the Remez exchange algorithm.

# Arguments

  * `numtaps::Integer`: The desired number of taps in the filter.    The number of taps is the number of terms in the filter, or the filter    order plus one.
  * `bands_defs`: A sequence of band definitions.   This sequence defines the bands. Each entry is a pair. The pair's   first item is a tuple of band edges (low, high). The pair's second item    defines the desired response and weight in that band. The weight is optional   and defaults to 1.0. Both the desired response and weight may be either scalars   or functions. If a function, the function should accept a real frequency and   return the real desired response or real weight. Examples:

      * LPF with unity weights. `[(0, 0.475) => 1, (0.5, 1.0) => 0]`
      * LPF with weight of 2 in the stop band. `[(0, 0.475) => (1, 1), (0.5, 1.0) => (0, 2)]`
      * BPF with unity weights. `[(0, 0.375) => 0, (0.4, 0.5) => 1, (0.525, 1.0) => 0]`
      * Hilbert transformer. `[(0.1, 0.95) => 1]; neg=true`
      * Differentiator. `[(0.01, 0.99) => (f -> f/2, f -> 1/f)]; neg=true`
  * `Hz::Real`: The sampling frequency in Hz. Default is 1.
  * `neg::Bool`: Whether the filter has negative symmetry or not. Default is false.   If false, the filter is even-symmetric. If true, the filter is odd-symmetric.   neg=true means that h[n]=-h[end+1-n]; neg=false means that h[n]=h[end+1-n].
  * `maxiter::Integer`: (optional)   Maximum number of iterations of the algorithm. Default is 25.
  * `grid_density:Integer`: (optional)   Grid density. The dense grid used in `remez` is of size   `(numtaps + 1) * grid_density`. Default is 16.

# Returns

  * `h::Array{Float64,1}`: A rank-1 array containing the coefficients of the optimal   (in a minimax sense) filter.

[^McClellan1973a]: 

J. H. McClellan and T. W. Parks, A unified approach to the design of optimum FIR linear phase digital filters, IEEE Trans. Circuit Theory, vol. CT-20, pp. 697-701, 1973.

[^McClellan1973b]: 

J. H. McClellan, T. W. Parks and L. R. Rabiner, A Computer Program for Designing Optimum FIR Linear Phase Digital Filters, IEEE Trans. Audio Electroacoust., vol. AU-21, pp. 506-525, 1973.

# Examples

Construct a length 35 filter with a passband at 0.15-0.4 Hz  (desired response of 1), and stop bands at 0-0.1 Hz and 0.45-0.5 Hz (desired response of 0). Note: the behavior in the frequency ranges between  those bands - the transition bands - is unspecified.

```jldoctest; setup = :(using DSP)
julia> bpass = remez(35, [(0, 0.1)=>0, (0.15, 0.4)=>1, (0.45, 0.5)=>0]);
```

You can trade-off maximum error achieved for transition bandwidth.  The wider the transition bands, the lower the maximum error in the bands specified. Here is a bandpass filter with the same passband, but wider transition bands.

```jldoctest; setup = :(using DSP)
julia> bpass2 = remez(35, [(0, 0.08)=>0, (0.15, 0.4)=>1, (0.47, 0.5)=>0]);
```

Here we compute the frequency responses and plot them in dB.

```julia-repl
julia> using PyPlot
julia> b = DSP.Filters.PolynomialRatio(bpass, [1.0])
julia> b2 = DSP.Filters.PolynomialRatio(bpass2, [1.0])
julia> f = range(0, stop=0.5, length=1000)
julia> plot(f, 20*log10.(abs.(freqresp(b,f,1.0))))
julia> plot(f, 20*log10.(abs.(freqresp(b2,f,1.0))))
julia> grid()
```

# Examples from the unittests - standard (even) symmetry.

Length 151 LPF (Low Pass Filter).

```jldoctest; setup = :(using DSP)
julia> h = remez(151, [(0, 0.475) => 1, (0.5, 1.0) => 0]; Hz=2.0);
```

Length 152 LPF. Non-default "weight" input.

```jldoctest; setup = :(using DSP)
julia> h = remez(152, [(0, 0.475) => (1, 1), (0.5, 1.0) => (0, 2)]; Hz=2.0);
```

Length 51 HPF (High Pass Filter).

```jldoctest; setup = :(using DSP)
julia> h = remez(51, [(0, 0.75) => 0, (0.8, 1.0) => 1]; Hz=2.0);
```

Length 180 BPF (Band Pass Filter).

```jldoctest; setup = :(using DSP)
julia> h = remez(180, [(0, 0.375) => 0, (0.4, 0.5) => 1, (0.525, 1.0) => 0]; Hz=2.0, maxiter=30);
```

# Examples from the unittests - Odd-symmetric filters - hilbert and differentiators type.

Even length - has a much better approximation since the response is not constrained to 0 at the nyquist frequency.  Length 20 Hilbert transformer.

```jldoctest; setup = :(using DSP)
julia> h = remez(20, [(0.1, 0.95) => 1]; neg=true, Hz=2.0);
```

Length 21 Hilbert transformer.

```jldoctest; setup = :(using DSP)
julia> h = remez(21, [(0.1, 0.95) => 1]; neg=true, Hz=2.0);
```

Length 200 differentiator.

```jldoctest; setup = :(using DSP)
julia> h = remez(200, [(0.01, 0.99) => (f -> f/2, f -> 1/f)]; neg=true, Hz=2.0);
```

Length 201 differentiator.

```jldoctest; setup = :(using DSP)
julia> h = remez(201, [(0.05, 0.95) => (f -> f/2, f -> 1/f)]; neg=true, Hz=2.0);
```

Inverse sinc filter - custom response function

```julia-repl
julia> L = 64; Fs = 4800*L;
julia> passband_response_function = f -> (f==0) ? 1.0 : abs.((π*f/4800) ./ sin.(π*f/4800));
julia> h = remez(201, [(    0.0, 2880.0) => (passband_response_function, 1.0),
                (10000.0,   Fs/2) => (0.0, 100.0)]; Hz=Fs);
```
