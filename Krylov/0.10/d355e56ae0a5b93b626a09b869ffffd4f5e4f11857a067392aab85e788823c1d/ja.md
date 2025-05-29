```
V, β, H = arnoldi(A, b, k; allow_breakdown=false, reorthogonalization=false)
```

#### 入力引数

  * `A`: 次元 `n` の正方行列をモデル化する線形演算子;
  * `b`: 長さ `n` のベクトル;
  * `k`: アーノルディ過程の反復回数.

#### キーワード引数

  * `allow_breakdown`: 正確なブレイクダウンが発生したときにプロセスを続行するか、エラーを発生させるかを指定します;
  * `reorthogonalization`: クライロフ基底に新たに追加された各ベクトルをすべての以前のベクトルに対して再直交化します（完全再直交化）.

#### 出力引数

  * `V`: 密な `n × (k+1)` 行列;
  * `β`: `βv₁ = b` となる係数;
  * `H`: 密な `(k+1) × k` 上ヘッセンベルク行列.

#### 参考文献

  * W. E. Arnoldi, [*The principle of minimized iterations in the solution of the matrix eigenvalue problem*](https://doi.org/10.1090/qam/42792), Quarterly of Applied Mathematics, 9, pp. 17–29, 1951.
