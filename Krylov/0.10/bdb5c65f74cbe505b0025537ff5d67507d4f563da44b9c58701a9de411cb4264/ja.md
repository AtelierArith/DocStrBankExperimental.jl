```
V, β, T, U, γᴴ, Tᴴ = nonhermitian_lanczos(A, b, c, k; allow_breakdown=false)
```

#### 入力引数

  * `A`: 次元 `n` の正方行列をモデル化する線形演算子;
  * `b`: 長さ `n` のベクトル;
  * `c`: 長さ `n` のベクトル;
  * `k`: 非エルミート・ランチョス法の反復回数.

#### キーワード引数

  * `allow_breakdown`: 正確なブレイクダウンが発生した場合にプロセスを続行するか、エラーを発生させるかを指定します.

#### 出力引数

  * `V`: 密な `n × (k+1)` 行列;
  * `β`: `βv₁ = b` となる係数;
  * `T`: 疎な `(k+1) × k` 三重対角行列;
  * `U`: 密な `n × (k+1)` 行列;
  * `γᴴ`: `γᴴu₁ = c` となる係数;
  * `Tᴴ`: 疎な `(k+1) × k` 三重対角行列.

#### 参考文献

  * C. Lanczos, [*An Iteration Method for the Solution of the Eigenvalue Problem of Linear Differential and Integral Operators*](https://doi.org/10.6028/jres.045.026), Journal of Research of the National Bureau of Standards, 45(4), pp. 225–280, 1950.
  * H. I. van der Veen and K. Vuik, [*Bi-Lanczos with partial orthogonalization*](https://doi.org/10.1016/0045-7949(94)00565-K), Computers & structures, 56(4), pp. 605–613, 1995.
