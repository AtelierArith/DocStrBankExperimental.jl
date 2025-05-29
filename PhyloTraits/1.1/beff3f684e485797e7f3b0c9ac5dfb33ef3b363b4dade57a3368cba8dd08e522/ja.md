```
HKY85(rate, pi, relative)
```

Hasegawa et al. 1985の置換モデルに基づく核酸置換モデルです。`rate`は1または2のレートのベクトルであり、`pi`は1に合計される4つの確率のベクトルです。

`relative`がfalseの場合、2つのレートは遷移率と逆遷移率、αとβを表します。`relative`がtrue（デフォルト）の場合、最初のレートのみが使用され、遷移/逆遷移比を表します：κ=α/β。レート遷移行列Qは、平均して1回の変化/単位時間を持つように正規化されます。つまり、Qの絶対バージョンは`2(piT*piC + piA*piG)α + 2(piY*piR)β`で割られます。

`nparams`は1または2を返します。言い換えれば：定常分布はパラメータの数にカウントされず（`fitdiscrete`は現時点でpiの値を最適化しません）。

# 例

```jldoctest
julia> m1 = HKY85([.5], [0.20, 0.30, 0.30, 0.20])
HKY85 Substitution Model base frequencies: [0.2, 0.3, 0.3, 0.2]
relative rate version with transition/tranversion ratio kappa = 0.5,
 scaled so that there is one substitution per unit time
rate matrix Q:
               A       C       G       T
       A       *  0.4839  0.2419  0.3226
       C  0.3226       *  0.4839  0.1613
       G  0.1613  0.4839       *  0.3226
       T  0.3226  0.2419  0.4839       *

julia> nstates(m1)
4

julia> m2 = HKY85([0.5, 0.5], [0.20, 0.30, 0.30, 0.20], false)
HKY85 Substitution Model base frequencies: [0.2, 0.3, 0.3, 0.2]
absolute rate version with transition/transversion ratio kappa = a/b = 1.0
 with rates a = 0.5 and b = 0.5
rate matrix Q:
               A       C       G       T
       A       *  0.1500  0.1500  0.1000
       C  0.1000       *  0.1500  0.1000
       G  0.1000  0.1500       *  0.1000
       T  0.1000  0.1500  0.1500       *

```
