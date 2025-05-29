```
squeeze([T=ComplexF64,] b::SpinBasis, z)
```

圧縮演算子 $S(z)=\exp{\left(\frac{z^*\hat{J_-}^2 - z\hat{J}_+}{2 N}\right)}$ は、指定されたスピン-$N/2$ 基底に対して、オプションのデータ型 `T` で計算され、行列指数関数として計算されます。過度の圧縮 ($|z| > \sqrt{N}$) は、過圧縮状態を生成します。
