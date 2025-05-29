```
struct PEP <: AbstractSPMF
function PEP(AA::Vector{AbstractMatrix})
```

型 `PEP` はそのモノミアル係数を介して多項式固有値問題を定義します。多項式固有値問題 (PEP) は次の和によって定義されます。

$$
Σ_i A_i λ^i,
$$

ここで $i = 0,1,2,$ であり、すべての行列はサイズ $n×n$ です。ベクトル `AA` には $A_1,...$ が含まれています。

# 例

```julia-repl
julia> A0=[1.0 3; 4 5]; A1=A0.+one(2); A2=ones(2,2);
julia> pep=PEP([A0,A1,A2])
julia> compute_Mder(pep,3)-(A0+A1*3+A2*9)
2×2 Array{Float64,2}:
 0.0  0.0
 0.0  0.0
```

さらに [`polyeig`](methods.md#NonlinearEigenproblems.NEPSolver.polyeig), [`companion`](methods.md#NonlinearEigenproblems.NEPSolver.companion), [`ChebPEP`](@ref), [`interpolate`](@ref) を参照してください。
