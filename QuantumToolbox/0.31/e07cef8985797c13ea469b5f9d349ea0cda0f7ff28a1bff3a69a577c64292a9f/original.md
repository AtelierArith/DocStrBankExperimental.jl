```
jmat(j::Real, which::Union{Symbol,Val})
```

Generate higher-order Spin-`j` operators, where `j` is the spin quantum number and can be a non-negative integer or half-integer

The parameter `which` specifies which of the following operator to return.

  * `:x`: $\hat{S}_x$
  * `:y`: $\hat{S}_y$
  * `:z`: $\hat{S}_z$
  * `:+`: $\hat{S}_+$
  * `:-`: $\hat{S}_-$

Note that if the parameter `which` is not specified, returns a set of Spin-`j` operators: $(\hat{S}_x, \hat{S}_y, \hat{S}_z)$

# Examples

```jldoctest
julia> jmat(0.5, :x)

Quantum Object:   type=Operator()   dims=[2]   size=(2, 2)   ishermitian=true
2×2 SparseMatrixCSC{ComplexF64, Int64} with 2 stored entries:
     ⋅      0.5+0.0im
 0.5+0.0im      ⋅

julia> jmat(0.5, Val(:-))

Quantum Object:   type=Operator()   dims=[2]   size=(2, 2)   ishermitian=false
2×2 SparseMatrixCSC{ComplexF64, Int64} with 1 stored entry:
     ⋅          ⋅    
 1.0+0.0im      ⋅

julia> jmat(1.5, Val(:z))

Quantum Object:   type=Operator()   dims=[4]   size=(4, 4)   ishermitian=true
4×4 SparseMatrixCSC{ComplexF64, Int64} with 4 stored entries:
 1.5+0.0im      ⋅           ⋅           ⋅    
     ⋅      0.5+0.0im       ⋅           ⋅    
     ⋅          ⋅      -0.5+0.0im       ⋅    
     ⋅          ⋅           ⋅      -1.5+0.0im
```

!!! warning "Beware of type-stability!"
    If you want to keep type stability, it is recommended to use `jmat(j, Val(which))` instead of `jmat(j, which)`. See [this link](https://docs.julialang.org/en/v1/manual/performance-tips/#man-performance-value-type) and the [related Section](@ref doc:Type-Stability) about type stability for more details.

