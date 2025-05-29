```
(1) randUnitaryMat(n::Int)
(2) randUnitaryMat(::Type{Complex{T}}, n::Int)
```

**エイリアス**: `randOrthMat`, `randU`

ランダムな $n⋅n$

  * (1) [直交](https://bit.ly/2vrr0wU) 行列 (実数)
  * (2) [ユニタリ](https://bit.ly/2JCHbmC) 行列 (複素数)

行列は、ランダムなガウス要素で埋められた $n⋅n$ 行列に対して修正された（安定化された）[グラム・シュミット直交化](https://bit.ly/2YE6zvy) 手法（[`mgs`](@ref)）を実行することで生成されます。

**関連項目**: `randΛ` ([`randEigvals`](@ref)), `randP` ([`randPosDefMat`](@ref)).

**例**

```julia
using PosDefManifold
n=3;
X=randU(n)*sqrt(randΛ(n))*randU(n)'  # (1) ランダムな正方行列を生成

U=randU(ComplexF64, n);
V=randU(ComplexF64, n);
Y=U*sqrt(randΛ(n))*V' # (2) ランダムな正方複素行列を生成
```
