```
shrinkage(x, λ, A, b)
```

一般化収縮演算子をスケーリングパラメータ `λ` で `x` に対して計算します。これは、二次関数の近接演算子で、二次パラメータ `A` と線形パラメータ `b` を持ちます。

#### 引数

  * `x::AbstractVector` : 入力
  * `λ::Real`           : スケーリングパラメータ
  * `A::AbstractMatrix` : 二次係数
  * `b::AbstractVector` : 線形係数

#### 戻り値

  * `y::AbstractVector` : 縮小された値

```
