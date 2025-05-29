```
kiops(tstops, A, u; kwargs...) -> (w, stats)
```

ベクトル `u` からの作用を受ける $φ$ 関数の線形結合を評価します。すなわち、

$$
  w(i) = φ_0(t[i] A) u[:, 1] + φ_1(t[i] A) u[:, 2] + φ_2(t[i] A) u[:, 3] + ...
$$

クライロフ部分空間のサイズは、積分中に動的に変更されます。クライロフ部分空間は、不完全直交化法を使用して計算されます。

引数:

  * `tstops`     - `tstop` の配列
  * `A`          - $φ$ 関数の行列引数
  * `u`          - $φ$ 関数によって掛けられるベクトルを表す列を持つ行列

キーワード引数:

  * `tol`        - 必要な収束許容誤差 (デフォルト: 1e-7)
  * `mmin`, `mmax` - クライロフサイズを mmin と mmax の間で変動させる (デフォルト: 10, 128)
  * `m`          - 適切なクライロフサイズの推定 (デフォルト: mmin)
  * `iop`        - 不完全直交化手続きの長さ (デフォルト: 2)
  * `ishermitian` - $A$ がエルミートかどうか (デフォルト: ishermitian(A))
  * `opnorm`     - $A$ の演算子ノルム (デフォルト: opnorm(A, Inf))
  * `task1`      - true の場合、結果を 1/T^p で割る

戻り値:

  * `w`        - ベクトル `u` からの作用を受ける $φ$ 関数の線形結合
  * `stats[1]` - サブステップの数
  * `stats[2]` - 拒否されたステップの数
  * `stats[3]` - クライロフステップの数
  * `stats[4]` - 行列指数の数
  * `stats[5]` - 最後のサブステップのクライロフサイズ

`n` は元の問題のサイズ、`p` は $φ$ 関数の最高インデックスです。

参考文献:

  * Gaudreault, S., Rainwater, G. and Tokman, M., 2018. KIOPS: A fast adaptive Krylov subspace solver for exponential integrators. Journal of Computational Physics. Based on the PHIPM and EXPMVP codes (http://www1.maths.leeds.ac.uk/~jitse/software.html). https://gitlab.com/stephane.gaudreault/kiops.
  * Niesen, J. and Wright, W.M., 2011. A Krylov subspace method for option pricing. SSRN 1799124
  * Niesen, J. and Wright, W.M., 2012. Algorithm 919: A Krylov subspace algorithm for evaluating the $φ$-functions appearing in exponential integrators. ACM Transactions on Mathematical Software (TOMS), 38(3), p.22

```
