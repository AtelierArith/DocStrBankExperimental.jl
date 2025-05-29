```
plan_laplacian(dims::Tuple,[with_inverse=false],[fftw_flags=FFTW.ESTIMATE],
                      [factor=1.0],[dx=1.0],[dtype=Float64])
```

Constructor to set up an operator for evaluating the discrete Laplacian on dual or primal nodal data of dimension `dims`. If the optional keyword `with_inverse` is set to `true`, then it also sets up the inverse Laplacian (the lattice Green's function, LGF). These can then be applied, respectively, with `*` and `\` operations on data of the appropriate size. The optional parameter `factor` is a scalar used to multiply the result of the operator and divide the inverse. The optional parameter `dx` is used in adjusting the uniform value of the LGF to match the behavior of the continuous analog at large distances; this is set to 1.0 by default. The type of data on which to act is floating point by default, but can also be ComplexF64. This is specified with the optional parameter `dtype`

Instead of the first argument, one can also supply `w::Nodes` to specify the size of the domain.

# Example

```jldoctest
julia> w = Nodes(Dual,(5,5));

julia> w[3,3] = 1.0;

julia> L = plan_laplacian(5,5;with_inverse=true)
Discrete Laplacian (and inverse) on a (nx = 5, ny = 5) grid acting on Float64 data with spacing 1.0

julia> s = L\w
Nodes{Dual,5,5,Float64} data
Printing in grid orientation (lower left is (1,1))
5×5 Array{Float64,2}:
 0.16707    0.129276     0.106037     0.129276    0.16707
 0.129276   0.0609665   -0.00734343   0.0609665   0.129276
 0.106037  -0.00734343  -0.257343    -0.00734343  0.106037
 0.129276   0.0609665   -0.00734343   0.0609665   0.129276
 0.16707    0.129276     0.106037     0.129276    0.16707

julia> L*s ≈ w
true
```
