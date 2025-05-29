```
nfft_adjoint_direct(P::NFFT{D})
```

は、提供されたノード $\pmb{x}_j, j =1,2,\dots,M,$ が `P.X` にあり、係数 $f_j \in \mathbb{C}, j =1,2,\dots,M,$ が `P.f` にある場合に、単純な行列-ベクトル乗算を介して随伴NDFTを計算します。

# 入力

  * `P` - NFFTプラン構造。

# 参照

[`NFFT{D}`](@ref), [`nfft_adjoint`](@ref)
