```
nfst_trafo(P)
```

は、提供されたノード $\pmb{x}_j, j =1,2,\dots,M,$ が `P.X` にあり、係数 $\hat{f}_{\pmb{k}}^s \in \mathbb{R}, \pmb{k} \in I_{\pmb{N},s}^D,$ が `P.fhat` にある場合に、迅速な NFST アルゴリズムを使用して NDST を計算します。

# 入力

  * `P` - NFST プラン構造。

# 参照

[`NFST{D}`](@ref), [`nfst_trafo_direct`](@ref)
