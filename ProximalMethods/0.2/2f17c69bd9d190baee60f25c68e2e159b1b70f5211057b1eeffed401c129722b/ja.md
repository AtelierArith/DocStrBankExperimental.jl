```
shrinkage(x, λ, fac, b)
```

一般化収縮演算子をスケーリングパラメータ `λ` で `x` に対して計算します。これは、二次関数の近接演算子で、二次パラメータ `A` と線形パラメータ `b` を使用し、$I + λA$ の因子分解 `fac` を用います。

#### 引数

  * `x::AbstractVector` : 入力
  * `λ::Real`           : スケーリングパラメータ
  * `fac::Factorization`: $I + λA$ の因子分解
  * `b::AbstractVector` : 線形係数

#### 戻り値

  * `y::AbstractVector` : 縮小された値
