```
fastExpm(A)
fastExpm(A; threshold=1e-6)
fastExpm(A; nonzero_tol=1e-14)
fastExpm(A; threshold=1e-6, nonzero_tol=1e-14)
```

この関数は、スパースおよびフル行列のための行列指数関数を効率的に実装します。このコードは、スケーリング、テイラー級数、および二乗法に基づいています。現在はCPU上でのみ動作します。

計算を高速化し、スパース性を保持するために、2つのオプションのキーワード引数が使用されます。[1] thresholdはテイラー級数の閾値を決定します（デフォルトは1e-6）：例として、fastExpm(A, threshold=1e-10)があります。[2] nonzero*tolは、各計算ステップでnonzero*tolより小さい要素を削除してスパース性を保持します（デフォルトは1e-14）、例として、fastExpm(A, nonzero_tol=1e-10)があります。スパース性が25%未満の場合、コードは自動的にスパースからフルに切り替わり、速度を維持します。

このコードはもともとIlya Kuprov（http://spindynamics.org/）によって開発され、F. Mentink-Vigier（fmentink@magnet.fsu.edu）およびMurari Soundararajan（murari@magnet.fsu.edu）によって適応されました。このコードを使用する場合は、以下を引用してください。

  * H. J. Hogben, M. Krzystyniak, G. T. P. Charnock, P. J. Hore および I. Kuprov, Spinach – 大規模スピンシステムにおけるスピンダイナミクスのシミュレーションのためのソフトウェアライブラリ, J. Magn. Reson., 2011, 208, 179–194.
  * I. Kuprov, 大規模スピンシステムのためのスピン緩和理論の対角化なしの実装, J. Magn. Reson., 2011, 209, 31–38.
