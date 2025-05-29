`SPerm(M::AbstractMatrix,N::AbstractMatrix;dims)`

returns  a signed  permutation `p`  such that  `invpermute(N,p;dims)==M` if such  a `p` exists,  and `nothing` otherwise.  If `dims=(1,2)` then `M` and `N` should be symmetric matrices.

The  case `dims=(1,2)` routine is useful  to identify two objects which are isomorphic  but with different labelings. It  is used in Chevie to identify Lusztig  Fourier transform  matrices with  standard (classified)  data. The program  uses sophisticated algorithms, and can often handle matrices up to 80×80.

```julia-repl
julia> p=sperm"(1,-1)(2,5,3,-4,-2,-5,-3,4)(7,-9)";

julia> m=onmats(n,p);

julia> onmats(n,SPerm(m,n;dims=(1,2)))==m
true
```
