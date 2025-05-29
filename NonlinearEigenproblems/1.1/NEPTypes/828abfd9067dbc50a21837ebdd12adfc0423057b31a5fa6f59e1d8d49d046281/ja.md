```
struct LowRankFactorizedNEP <: AbstractSPMF
function LowRankFactorizedNEP(L::Vector,U::Vector,f::Vector)
function LowRankFactorizedNEP(L::Vector,U::Vector,A::Vector, f::Vector)
```

低ランクの `NEP` の表現であり、各項が因子分解されている `SPMF` であるという意味です：`A[i]=L[i]*U[i]'`。因子分解は `L` と `U` ベクトルで提供され、完全な行列 `A[i]` は提供されるか、そうでなければ暗黙的に計算されます。

# 例:

```
julia> L=randn(5,1); U=randn(5,1);
julia> f=S->exp(S)
julia> nep=LowRankFactorizedNEP([L],[U],[f]);
julia> X=randn(5,2);
julia> norm(compute_Mlincomb(nep,0.0,X)-L*U'*X*ones(2),1)
6.661338147750939e-16
```
