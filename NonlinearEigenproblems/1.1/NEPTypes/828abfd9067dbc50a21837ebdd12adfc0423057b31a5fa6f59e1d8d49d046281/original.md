```
struct LowRankFactorizedNEP <: AbstractSPMF
function LowRankFactorizedNEP(L::Vector,U::Vector,f::Vector)
function LowRankFactorizedNEP(L::Vector,U::Vector,A::Vector, f::Vector)
```

Representation of a `NEP` which has low rank in the sense that it is an `SPMF` where each of the terms are factorized: `A[i]=L[i]*U[i]'`. The factorization is provided in the `L` and `U` vectors and the full matrix `A[i]` can be either provided (or is otherwise implicitly computed).

# Example:

```
julia> L=randn(5,1); U=randn(5,1);
julia> f=S->exp(S)
julia> nep=LowRankFactorizedNEP([L],[U],[f]);
julia> X=randn(5,2);
julia> norm(compute_Mlincomb(nep,0.0,X)-L*U'*X*ones(2),1)
6.661338147750939e-16
```
