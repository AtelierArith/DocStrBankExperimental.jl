```
finufft_makeplan(type::Integer,
                 n_modes_or_dim::Union{Array{Int64},Integer},
                 iflag::Integer,
                 ntrans::Integer,
                 eps::Real;
                 dtype=Float64,
                 kwargs...) -> plan::finufft_plan{dtype}
```

Creates a `finufft_plan` object for the guru interface to FINUFFT, of  type 1, 2 or 3, and with given numbers of Fourier modes (unless type 3).

# Inputs

  * `type`            transform type: 1, 2, or 3
  * `n_modes_or_dim`  if `type` is 1 or 2, the number of Fourier modes in each                 dimension: `ms` in 1D, `[ms mt]` in 2D, or `[ms mt mu]` in 3D.                 Its length thus sets the dimension, which must be 1, 2 or 3.                 If `type` is 3, in contrast, its *value* fixes the dimension.
  * `iflag`   if >=0, uses + sign in exponential, otherwise - sign.
  * `ntrans`          number of transforms to compute simultaneously
  * `eps`     relative precision requested (generally between 1e-15 and 1e-1),         real, need not match type of `dtype`
  * `dtype`           `Float32` or `Float64`, plan for single precision or double precision
  * `kwargs`  (optional): for options, see `nufft_opts` and https://finufft.readthedocs.io/en/latest/opts.html

# Returns

  * finufft_plan struct

# Examples

```julia-repl
julia> p = finufft_makeplan(2,10,+1,1,1e-6);
```

creates a plan for a 1D type 2 Float64 transform with 10 Fourier modes and tolerance 1e-6.

```julia-repl
julia> p = finufft_makeplan(1,[10 20],+1,1,1e-6);
```

creates a plan for a 2D type 1 Float64 transform with 10*20 Fourier modes.

```julia-repl
julia> p = finufft_makeplan(3,2,+1,1,1e-4,dtype=Float32,nthreads=4);
```

creates a plan for a 2D type 3 Float32 transform with tolerance 1e-4, to use 4 threads.
