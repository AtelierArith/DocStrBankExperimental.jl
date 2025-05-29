```
squeeze([T=ComplexF64,] b::FockBasis, z)
```

指定されたフォック空間に対する圧縮演算子 $S(z)=\exp{\left(\frac{z^*\hat{a}^2-z\hat{a}^{\dagger2}}{2}\right)}$ は、オプションのデータ型 `T` を持ち、有限次元（切り捨てられた）生成および消滅演算子の行列指数として計算されます。
