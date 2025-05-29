```
struct CORKPencil
function CORKPencil(M,N,Av,Bv,Z);
function CORKPencil(nep,is)
```

The struct `CORKPencil` represents a pencil with a particular structure, as given in the reference. The data can either be constructed directly via the first constructor, or from a NEP in the second constructor. The second constructor takes a `NEP` and  `is` which specifies a CORK-structure as well as an approximation method. This can be objects of the type `IarCorkLinearization` or `NleigsCorkLinearization`, which are the CORK-linearizations equivalent to (certain versions of) [`iar`](@ref) and [`nleigs`](@ref).

See [`buildPencil`](@ref) how to build standard pencil.

# Example:

The following example constructs a  `CORKPencil` from a general NEP and then computes approximations of NEPs by the interpolation approach of `nleigs`.

```julia-repl
julia> using LinearAlgebra
julia> A=(1:4)*(1:4)'+I; B=diagm(1 => [1,2,3]); C=ones(4,4);
julia> f1= λ-> one(λ);
julia> f2= λ-> λ;
julia> f3= λ-> exp(sin(λ/2));
julia> nep=SPMF_NEP([A,B,C],[f1,f2,f3]);
julia> cp=CORKPencil(nep,NleigsCorkLinearization());
julia> (A,B)=buildPencil(cp) # Form the pencil
julia> λv=eigen(A,B).values;
julia> λ=λv[sortperm(abs.(λv))[1]]; # Smallest eigval
julia> minimum(svdvals(compute_Mder(nep,λ))) # It's a solution
2.4364382475487156e-11
```

# References:

  * Compact rational Krylov methods for nonlinear eigenvalue problems SIAM Journal on Matrix Analysis and Applications, 36 (2), 820-838, 2015.

    ```

    ```
