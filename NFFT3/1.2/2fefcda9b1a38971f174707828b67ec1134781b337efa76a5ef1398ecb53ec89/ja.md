```
nfft_adjoint(P::NFFT{D})
```

は、提供されたノード $\pmb{x}_j, j =1,2,\dots,M,$ が `P.X` にあり、係数 $f_j \in \mathbb{C}, j =1,2,\dots,M,$ が `P.f` にある場合に、迅速な随伴 NFFT アルゴリズムを使用して随伴 NDFT を計算します。

# 入力

  * `P` - NFFT プラン構造。

# 参照

[`NFFT{D}`](@ref), [`nfft_adjoint_direct`](@ref)
