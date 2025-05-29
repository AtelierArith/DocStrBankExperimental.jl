```
V, β, T = hermitian_lanczos(A, b, k; allow_breakdown=false, reorthogonalization=false)
```

#### 入力引数

  * `A`: 次元 `n` のエルミート行列をモデル化する線形演算子;
  * `b`: 長さ `n` のベクトル;
  * `k`: エルミート・ランチョス法の反復回数.

#### キーワード引数

  * `allow_breakdown`: 正確なブレイクダウンが発生した場合にプロセスを続行するか、エラーを発生させるかを指定します;
  * `reorthogonalization`: クライロフ基底に新たに追加された各ベクトルを、前の2つのベクトルに対してのみ再直交化します（局所再直交化）.

#### 出力引数

  * `V`: 密な `n × (k+1)` 行列;
  * `β`: `βv₁ = b` となる係数;
  * `T`: 疎な `(k+1) × k` トリディアゴナル行列.

#### 参考文献

  * C. Lanczos, [*An Iteration Method for the Solution of the Eigenvalue Problem of Linear Differential and Integral Operators*](https://doi.org/10.6028/jres.045.026), Journal of Research of the National Bureau of Standards, 45(4), pp. 225–280, 1950.
  * H. D. Simon, [*The Lanczos algorithm with partial reorthogonalization*](https://doi.org/10.1090/S0025-5718-1984-0725988-X), Mathematics of computation, 42(165), pp. 115–142, 1984.
