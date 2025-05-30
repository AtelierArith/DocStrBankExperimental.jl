```
fista(env::Environment,b ,p [,f<:AbstractArray]; tol=1e-6, maxit=1000)
```

FISTAを使用して、`env.fn`のすべての周波数ビンまたは`f`の周波数に対して非負制約付きの逆畳み込みを実行します。`f`は、`env.fn`の値の正確な（部分）集合と一致する値を含む必要があります。

# 引数

*必須:*

  * `env::Environment`: 環境構造体
  * `b::FreqArray`: ビームフォーミング配列
  * `p::FreqArray`: 点拡散関数配列

*オプション:*

  * `tol`: 収束許容誤差（デフォルト: 1e-6）
  * `maxit`: 最大反復回数（デフォルト: 1000）

# 参考文献:

  * Beck, A., & Teboulle, M. (2009). A fast iterative shrinkage-thresholding algorithm for linear inverse problems.    SIAM journal on imaging sciences, 2(1), 183-202.
  * Lylloff, O., Fernández-Grande, E., Agerkvist, F., Hald, J., Tiana Roig, E., & Andersen, M. S. (2015). Improving the efficiency of deconvolution algorithms for sound source localization.    The journal of the acoustical society of America, 138(1), 172-180
