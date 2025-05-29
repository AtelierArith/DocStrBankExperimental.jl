```
V, β, H, U, γ, F = montoison_orban(A, B, b, c, k; allow_breakdown=false, reorthogonalization=false)
```

#### 入力引数

  * `A`: 次元 `m × n` の行列をモデル化する線形演算子;
  * `B`: 次元 `n × m` の行列をモデル化する線形演算子;
  * `b`: 長さ `m` のベクトル;
  * `c`: 長さ `n` のベクトル;
  * `k`: Montoison-Orban プロセスの反復回数。

#### キーワード引数

  * `allow_breakdown`: 正確なブレークダウンが発生したときにプロセスを続行するか、エラーを発生させるかを指定します;
  * `reorthogonalization`: 新しく追加されたクライロフ基底の各ベクトルをすべての以前のベクトルに対して再直交化します（完全再直交化）。

#### 出力引数

  * `V`: 密な `m × (k+1)` 行列;
  * `β`: `βv₁ = b` となる係数;
  * `H`: 密な `(k+1) × k` 上ヘッセンベルグ行列;
  * `U`: 密な `n × (k+1)` 行列;
  * `γ`: `γu₁ = c` となる係数;
  * `F`: 密な `(k+1) × k` 上ヘッセンベルグ行列。

#### 参考文献

  * A. Montoison and D. Orban, [*GPMR: An Iterative Method for Unsymmetric Partitioned Linear Systems*](https://doi.org/10.1137/21M1459265), SIAM Journal on Matrix Analysis and Applications, 44(1), pp. 293–311, 2023.
