```julia
    matP(ς::Vector{T}) where T<:RealOrComplex
```

*マトリゼ* 接ベクトル (ベクトル) ς :  vec -> mat.

これは [`vecP`](@ref) 関数を逆にする関数であり、したがってそこに適用される重み付けも逆になります。

もし $ς=vecP(S)$ であり、$S$ が $n⋅n$ ヘルミート行列または対称行列であるなら、$ς$ はサイズ $n(n+1)/2$ の接ベクトルです。`matP(ς)` を呼び出す結果は $n⋅n$ 行列 $S$ になります。$S$ は常に `Hermitian` としてフラグ付けされて返されます。

**やること**: この関数はより効率的に書き直すことができます。

**例**

```julia
using PosDefManifold
P=randP(3)
Q=randP(3)
G=mean(Fishr, P, Q)
# フィッシャー平均基準点での接空間に P を投影
S=logMap(Fisher, P, G)
# S をベクトル化
v=vecP(S)
# 直交行列でベクトルを回転
n=Int(size(S, 1)*(size(S, 1)+1)/2)
U=randP(n)
z=U*v
# 接空間の点を取得
S=matP(z)
```
