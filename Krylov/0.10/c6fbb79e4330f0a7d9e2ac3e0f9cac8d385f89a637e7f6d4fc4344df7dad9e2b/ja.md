```
V, U, β, L = golub_kahan(A, b, k; allow_breakdown=false)
```

#### 入力引数

  * `A`: 次元 `m × n` の行列をモデル化する線形演算子;
  * `b`: 長さ `m` のベクトル;
  * `k`: Golub-Kahan プロセスの反復回数.

#### キーワード引数

  * `allow_breakdown`: 正確なブレイクダウンが発生した場合にプロセスを続行するか、エラーを発生させるかを指定します.

#### 出力引数

  * `V`: 密な `n × (k+1)` 行列;
  * `U`: 密な `m × (k+1)` 行列;
  * `β`: `βu₁ = b` となる係数;
  * `L`: スパースな `(k+1) × (k+1)` 下三角バイダイアゴナル行列.

#### 参考文献

  * G. H. Golub と W. Kahan, [*行列の特異値と擬似逆行列の計算*](https://doi.org/10.1137/0702016), SIAM Journal on Numerical Analysis, 2(2), pp. 225–224, 1965.
  * C. C. Paige, [*行列のバイダイアゴナリゼーションと線形方程式の解法*](https://doi.org/10.1137/0711019), SIAM Journal on Numerical Analysis, 11(1), pp. 197–209, 1974.

```
