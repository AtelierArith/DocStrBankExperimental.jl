```julia
ExtrapolationMidpointHairerWanner(; max_order = 10,
                                    min_order = 2,
                                    init_order = 5,
                                    thread = OrdinaryDiffEq.True(),
                                    sequence = :harmonic,
                                    sequence_factor = 2)
```

Parallelized Explicit Extrapolation Method. Midpoint extrapolation using Barycentric coordinates,     following Hairer's ODEX in the adaptivity behavior.

### Keyword Arguments

  * `max_order`: maximum order of the adaptive order algorithm.
  * `min_order`: minimum order of the adaptive order algorithm.
  * `init_order`: initial order of the adaptive order algorithm.
  * `thread`: determines whether internal broadcasting on appropriate CPU arrays should be serial (`thread = OrdinaryDiffEq.False()`) or use multiple threads (`thread = OrdinaryDiffEq.True()`) when Julia is started with multiple threads.
  * `sequence`: the step-number sequences, also called the subdividing sequence. Possible values are `:harmonic`, `:romberg` or `:bulirsch`.
  * `sequence_factor`: denotes which even multiple of sequence to take while evaluating internal discretizations.

## References

@inproceedings{elrod2022parallelizing,   title={Parallelizing explicit and implicit extrapolation methods for ordinary differential equations},   author={Elrod, Chris and Ma, Yingbo and Althaus, Konstantin and Rackauckas, Christopher and others},   booktitle={2022 IEEE High Performance Extreme Computing Conference (HPEC)},   pages={1–9},   year={2022},   organization={IEEE}}
