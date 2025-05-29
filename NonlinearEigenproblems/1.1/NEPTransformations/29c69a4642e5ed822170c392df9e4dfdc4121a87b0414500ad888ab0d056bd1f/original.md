```
struct CORKPencilLR
function CORKPencilLR(M,N,Av,AvLR,Bv,BvLR,Z);
```

Represents / constructs a low-rank CORK-pencil. `AvLR`, `BvLR` and `Z` correspond to the low-rank factorization of terms `Av` and `Bv`. See [`CORKPencil`](@ref) and reference below.

# Example

The example illustrate a low-rank linearization of a Taylor expansion of the NEP $A0-λI+vv^Te^{-λ}$.

```julia-repl
julia> A0=[1.0 3.0; -1.0 2.0]/10;
julia> v=reshape([-1.0 ; 1]/sqrt(2),n,1);

julia> Av=[-A0-v*v']
julia> Bv=[-one(A0)-v*v']
julia> BvLR=[v/2, -v/3, v/4, -v/5, v/6, -v/7,  v/8, -v/9]
julia> AvLR=zero.(BvLR);
julia> Z=v;
julia> d=9;
julia> M=diagm( 0 =>  ones(d) )[2:end,:]
julia> N=diagm( -1 =>  1 ./ (1:d-1) )[2:end,:]
julia> cplr=CORKPencilLR(M,N,Av,AvLR,Bv,BvLR,Z);
julia> (AA,BB)=buildPencil(cplr);
julia> λ=eigen(AA,BB).values[end];
julia> minimum(svdvals(A0-λ*I+v*v'*exp(-λ)))
8.870165379112754e-13
```

# References:

  * Section 7 in Compact rational Krylov methods for nonlinear eigenvalue problems SIAM Journal on Matrix Analysis and Applications, 36 (2), 820-838, 2015.
