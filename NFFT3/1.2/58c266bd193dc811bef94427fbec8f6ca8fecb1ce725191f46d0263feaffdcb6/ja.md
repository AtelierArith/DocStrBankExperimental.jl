```
nfft_trafo(P::NFFT{D})
```

は、提供されたノード $\pmb{x}_j, j =1,2,\dots,M,$ を `P.X` から、係数 $\hat{f}_{\pmb{k}} \in \mathbb{C}, \pmb{k} \in I_{\pmb{N}}^D,$ を `P.fhat` から取得し、高速 NFFT アルゴリズムを用いて NDFT を計算します。

# 入力

  * `P` - NFFT プラン構造体。

# 参照

[`NFFT{D}`](@ref), [`nfft_trafo_direct`](@ref)
