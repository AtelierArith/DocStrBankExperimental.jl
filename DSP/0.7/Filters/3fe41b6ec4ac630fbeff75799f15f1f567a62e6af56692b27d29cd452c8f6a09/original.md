```
remez(numtaps::Integer, 
      bands::Vector, 
      desired::Vector; 
      weight::Vector=[], 
      Hz::Real=1.0, 
      filter_type::RemezFilterType=filter_type_bandpass,
      maxiter::Integer=25, 
      grid_density::Integer=16)
```

This is the scipy compatible version that requires 3 arguments (numtaps, bands, desired).  For a simplified API, see the 2 argument version (numtaps, band_defs). The filters designed are equivalent, the inputs are just specified in a different way. Below the arguments and examples are described that differ from the simplified API version.

# Arguments

  * `bands::Vector`: A monotonic sequence containing the band edges in Hz.   All elements must be non-negative and less than half the sampling   frequency as given by `Hz`.
  * `desired::Vector`:A sequence half the size of bands containing the desired    gain in each of the specified bands.
  * `weight::Vector`: (optional)   A relative weighting to give to each band region. The length of   `weight` has to be half the length of `bands`.
  * `filter_type::RemezFilterType`: Default is `filter_type_bandpass`.   The type of filter:

      * `filter_type_bandpass` : flat response in bands. This is the default.
      * `filter_type_differentiator` : frequency proportional response in bands.   Odd symetric as in `filter_type_hilbert` case, but with a linear sloping   desired response.
      * `filter_type_hilbert` : filter with odd symmetry, that is, type III             (for even order) or type IV (for odd order)             linear phase filters.

# Examples

Compare the examples with the simplified API and the Scipy API. Each of the following blocks first designs a filter using the  simplified (recommended) API, and then designs the same filter using the Scipy-compatible API.

```jldoctest; setup = :(using DSP)
julia> bpass = remez(35, [(0, 0.1)=>0, (0.15, 0.4)=>1, (0.45, 0.5)=>0]);

julia> bpass = remez(35, [0, 0.1, 0.15, 0.4, 0.45, 0.5], [0, 1, 0]);

```

```jldoctest; setup = :(using DSP)
julia> bpass2 = remez(35, [(0, 0.08)=>0, (0.15, 0.4)=>1, (0.47, 0.5)=>0]);

julia> bpass2 = remez(35, [0, 0.08, 0.15, 0.4, 0.47, 0.5], [0, 1, 0]);

```

```jldoctest; setup = :(using DSP)
julia> h = remez(20, [(0.1, 0.95) => 1]; neg=true, Hz=2.0);

julia> h = remez(20, [0.1, 0.95], [1]; filter_type=filter_type_hilbert, Hz=2.0);

```

```jldoctest; setup = :(using DSP)
julia> h = remez(200, [(0.01, 0.99) => (f -> f/2, f -> 1/f)]; neg=true, Hz=2.0);

julia> h = remez(200, [0.01, 0.99], [1]; filter_type=filter_type_differentiator, Hz=2.0);

```
