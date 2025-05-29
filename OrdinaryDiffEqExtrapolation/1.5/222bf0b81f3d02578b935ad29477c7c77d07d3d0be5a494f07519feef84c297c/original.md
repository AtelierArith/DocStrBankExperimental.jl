```julia
AitkenNeville(; max_order::Int = 10,
                min_order::Int = 1,
                init_order = 3,
                thread = OrdinaryDiffEq.False())
```

Parallelized Explicit Extrapolation Method. Euler extrapolation using Aitken-Neville with the Romberg Sequence.

### Keyword Arguments

  * `max_order`: maximum order of the adaptive order algorithm.
  * `min_order`: minimum order of the adaptive order algorithm.
  * `init_order`: initial order of the adaptive order algorithm.
  * `thread`: determines whether internal broadcasting on appropriate CPU arrays should be serial (`thread = OrdinaryDiffEq.False()`) or use multiple threads (`thread = OrdinaryDiffEq.True()`) when Julia is started with multiple threads.

## References

@inproceedings{elrod2022parallelizing,   title={Parallelizing explicit and implicit extrapolation methods for ordinary differential equations},   author={Elrod, Chris and Ma, Yingbo and Althaus, Konstantin and Rackauckas, Christopher and others},   booktitle={2022 IEEE High Performance Extreme Computing Conference (HPEC)},   pages={1–9},   year={2022},   organization={IEEE}}
