```
nfft_trafo_direct(P::NFFT{D})
```

は、提供されたノード $\pmb{x}_j, j =1,2,\dots,M,$ が `P.X` にあり、係数 $\hat{f}_{\pmb{k}} \in \mathbb{C}, \pmb{k} \in I_{\pmb{N}}^D,$ が `P.fhat` にある場合に、単純な行列-ベクトル乗算を介して NDFT を計算します。

# 入力

  * `P` - NFFT プラン構造体。

# 参照

[`NFFT{D}`](@ref), [`nfft_trafo`](@ref)
