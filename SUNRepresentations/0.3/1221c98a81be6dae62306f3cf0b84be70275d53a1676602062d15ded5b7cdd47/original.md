```
struct SUNIrrep{N} <: AbstractIrrep{SU{N}}
```

The irrep of SU(N) with highest weight `I`.

# Constructors

```
SUNIrrep(I::NTuple{N,Int})
SUNIrrep(args::Vararg{Int})
```

Constructs the `SU{N}` irrep with highest weight `I` or `args...`.

```
SUNIrrep{N}(name::AbstractString)
```

Constructs the `SU{N}` irrep with dimensional name `name`. Note that the parameter `N` is required to uniquely identify the irrep.

```
SUNIrrep(a::Vector{Int})
```

Constructs the `SU{N}` irrep with highest weight `a = [a₁, a₂, …, aₙ₋₁]`.
