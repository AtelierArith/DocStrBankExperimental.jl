```julia
    procrustes(P::ℍ{T}, Q::ℍ{T}, extremum="min") where T<:RealOrComplex
```

2つの正定値行列 $P$ と $Q$ が与えられたとき、デフォルトでは次の問題の解を返します。

$$
\textrm{argmin}_Uδ(P,U^HQU)
$$

,

ここで $U$ はユニタリ行列の集合の上で変化し、$δ(.,.)$ は距離またはダイバージェンス関数です。

$$
U^HQU
$$

は物理学では $Q$ の *ユニタリ軌道* と呼ばれます。

引数 `extremum` が "max" として渡されると、代わりに次の問題の解を返します。

$$
\textrm{argmax}_Uδ(P,U^HQU)
$$

。

$$
P
$$

と $Q$ は `Hermitian` としてフラグ付けされている必要があります。詳細は [typecasting matrices](@ref) を参照してください。

Bhatia と Congedo (2019)[🎓](@ref) で示されているように、[Fisher](@ref)、[logdet zero](@ref)、[Wasserstein](@ref) および Kullback-Leibler ダイバージェンス（[logdet α](@ref) を参照）を使用すると、$Q$ のユニタリ軌道からの $P$ への最良近似は $P$ と可換であり、驚くべきことに同じ閉じた形の表現を持ちます。すなわち、

argmin の場合は $U_Q^↓U_P^{↓H}$、argmax の場合は $U_Q^↑U_P^{↓H}$ です。

ここで、$U^↓$ は対応する固有値の *減少* 順にソートされた列に固有ベクトルを持つ引数の固有ベクトル行列を示し、$U^↑$ は対応する固有値の *増加* 順にソートされた列に固有ベクトルを持つ引数の固有ベクトル行列を示します。

同じ解は、[Euclidean](@ref) メトリックを使用して上記の極値問題を解くことによっても長い間知られています（Umeyama, 1988）。

一般化されたプロクルステス問題

$$
\textrm{argmin}_Usum_{i=1}^{k}δ(P_i,U^HQ_iU)
$$

は、Julia パッケージ [Manopt](https://github.com/kellertuer/Manopt.jl) を使用して解決できます。

**例**

```julia
using PosDefManifold
P=randP(3)
Q=randP(3)
# argmin 問題
U=procrustes(P, Q)
# argmax 問題
V=procrustes(P, Q, "max")
```
