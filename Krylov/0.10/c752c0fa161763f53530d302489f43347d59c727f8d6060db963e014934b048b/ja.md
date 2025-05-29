```
V, β, T, U, γᴴ, Tᴴ = saunders_simon_yip(A, b, c, k; allow_breakdown=false)
```

#### 入力引数

  * `A`: 次元 `m × n` の行列をモデル化する線形演算子;
  * `b`: 長さ `m` のベクトル;
  * `c`: 長さ `n` のベクトル;
  * `k`: Saunders-Simon-Yip プロセスの反復回数.

#### キーワード引数

  * `allow_breakdown`: 正確なブレイクダウンが発生したときにプロセスを続行するか、エラーを発生させるかを指定します.

#### 出力引数

  * `V`: 密な `m × (k+1)` 行列;
  * `β`: `βv₁ = b` となる係数;
  * `T`: 疎な `(k+1) × k` 三重対角行列;
  * `U`: 密な `n × (k+1)` 行列;
  * `γᴴ`: `γᴴu₁ = c` となる係数;
  * `Tᴴ`: 疎な `(k+1) × k` 三重対角行列.

#### 参考文献

  * M. A. Saunders, H. D. Simon, and E. L. Yip, [*Two Conjugate-Gradient-Type Methods for Unsymmetric Linear Equations*](https://doi.org/10.1137/0725052), SIAM Journal on Numerical Analysis, 25(4), pp. 927–940, 1988.
