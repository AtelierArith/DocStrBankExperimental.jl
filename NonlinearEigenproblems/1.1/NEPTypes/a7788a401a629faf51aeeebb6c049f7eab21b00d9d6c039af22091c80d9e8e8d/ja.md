```
type DEP <: AbstractSPMF
function DEP(AA::Vector{AbstractMatrix} [,tauv::Vector=[0,1.0]])
```

`DEP`（遅延固有値問題）は、次の和によって定義される問題です。

$$
M(λ)=-λI + Σ_i A_i exp(-τ_i λ)
$$

ここで、すべての行列はサイズ $n×n$ です。このタイプの NEP は、時間遅延システムの安定性を記述します。

構築はシステム行列 $A_i$ を取り、`tauv` は値 $τ_i$ のベクトルです。

# 例:

```julia-repl
julia> A0=randn(3,3); A1=randn(3,3);
julia> tauv=[0,0.2] # 遅延を持つベクトル
julia> dep=DEP([A0,A1],tauv)
julia> λ=3.0;
julia> M1=compute_Mder(dep,λ)
julia> M2=-λ*I+A0+A1*exp(-tauv[2]*λ)
julia> norm(M1-M2)
0.0
```
