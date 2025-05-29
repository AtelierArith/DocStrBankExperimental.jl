```
G2MomCorrelator(d::Int) <: AbstractOperator{ComplexF64}
```

距離 `d` における密度-密度相関を表す二体相関演算子です。`Complex` 値を返します。

単一成分内の相関:

$$
\hat{G}^{(2)}(d) = \frac{1}{M}\sum_{spqr=1}^M e^{-id(p-q)2π/M} a^†_{s} a^†_{p}  a_q a_r δ_{s+p,q+r}
$$

対角要素、すなわち `(p-q)=0` の場合は

$$
\frac{1}{M}\sum_{k,p=1}^M a^†_{k} b^†_{p}  b_p a_k .
$$

# 引数

  * `d::Integer`: 二つの粒子間の距離。

# 参照

  * [`Rimu.G2RealCorrelator`](@ref)
  * [`Rimu.G2RealSpace`](@ref)
  * [`Rimu.AbstractOperator`](@ref)
  * [`Rimu.AllOverlaps`](@ref)
