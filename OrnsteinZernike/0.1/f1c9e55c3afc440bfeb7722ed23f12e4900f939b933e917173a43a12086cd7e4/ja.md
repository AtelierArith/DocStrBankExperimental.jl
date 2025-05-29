```
ModifiedHypernettedChain <: Closure
```

修正ハイパーネットチェーン閉包を実装します $b(r) = b_{HS}(r) $。ここで $b_{HS}(r/σ)=\left((a_1+a_2x)(x-a_3)(x-a_4)/(a_3 a_4)\right)^2$ は $x<a_4$ の場合、$b_{HS}(r)=\left(A_1 \exp(-a_5(x-a_4))\sin(A_2(x-a_4))/r\right)^2$ は Malijevský & Labík によって見つかったハードスフィアブリッジ関数です。パラメータは次のように定義されます。

$$
x = r/σ-1
$$

$$
A_1 = (a_1+a_2 a_4)(a_4-a_3)(a_4+1)/(A_2 a_3 a_4)
$$

$$
A_2 =  \pi / (a_6 - a_4 - 1)
$$

$$
a_1 = \eta (1.55707 - 1.85633\eta) / (1-\eta)^2
$$

$$
a_2 = \eta (1.28127 - 1.82134\eta) / (1-\eta)
$$

$$
a_3 =  (0.74480 - 0.93453\eta)
$$

$$
a_4 = (1.17102 - 0.68230\eta)
$$

$$
a_5 = 0.15975/\eta^2
$$

$$
a_6 = (2.69757 - 0.86987\eta)
$$

ここで $\eta$ はハードスフィア参照系の体積分率です。この閉包は三次元の単一成分系にのみ機能します。デフォルトでは、$\sigma = 1.0$ です。

例:

```julia
closure = ModifiedHypernettedChain(0.4)
closure = ModifiedHypernettedChain(0.4; sigma=0.8)
```

参考文献:

Lado, F. "Perturbation correction for the free energy and structure of simple fluids." Physical Review A 8.5 (1973): 2548.

Malijevský, Anatol, and Stanislav Labík. "The bridge function for hard spheres." Molecular Physics 60.3 (1987): 663-669.
