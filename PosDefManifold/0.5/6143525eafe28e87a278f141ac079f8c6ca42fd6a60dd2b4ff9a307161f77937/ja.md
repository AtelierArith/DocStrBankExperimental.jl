```
fidelity(P::ℍ{T}, Q::ℍ{T}) where T<:RealOrComplex
```

2つの正定値 `Hermitian` 行列 $P$ と $Q$ が与えられたとき、彼らの *fidelity* を返します：

$$
tr\big(P^{1/2}QP^{1/2}\big)^{1/2}.
$$

これは量子物理学で使用され、[Wasserstein](@ref) メトリックに関連しています。例えば、Bhatia, Jain, and Lim (2019b)[🎓](@ref) を参照してください。

**例**

```julia
using PosDefManifold
P=randP(5);
Q=randP(5);
f=fidelity(P, Q)
```
