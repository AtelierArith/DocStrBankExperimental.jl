```
plan_intfact(a::Real,dims::Tuple,[fftw_flags=FFTW.ESTIMATE])
```

Constructor to set up an operator for evaluating the integrating factor with real-valued parameter `a`. This can then be applied with the `*` or `` operation on data of the appropriate size.

Note that `a` can be positive, negative, or zero. However, if `a` is negative, then only the $operation is actually correct; the `*` operation merely returns the identity to avoid excessive (and noisy) calculation. Similarly, if `a` is positive, the$ operation returns the identity. Thus, these operations are not inverses of one another. If `a` is zero, both operations return the identity.

The `dims` argument can be replaced with data of type `ScalarGridData` to specify the size of the domain.

# Example

```jldoctest
julia> w = Nodes(Dual,(6,6));

julia> w[4,4] = 1.0;

julia> E = plan_intfact(1.0,(6,6))
Integrating factor with parameter 1.0 on a (nx = 6, ny = 6) grid

julia> E*w
Nodes{Dual,6,6,Float64} data
Printing in grid orientation (lower left is (1,1))
6×6 Array{Float64,2}:
 0.00268447   0.00869352  0.0200715   0.028765    0.0200715   0.00869352
 0.00619787   0.0200715   0.0463409   0.0664124   0.0463409   0.0200715
 0.00888233   0.028765    0.0664124   0.0951774   0.0664124   0.028765
 0.00619787   0.0200715   0.0463409   0.0664124   0.0463409   0.0200715
 0.00268447   0.00869352  0.0200715   0.028765    0.0200715   0.00869352
 0.000828935  0.00268447  0.00619787  0.00888233  0.00619787  0.00268447
```
