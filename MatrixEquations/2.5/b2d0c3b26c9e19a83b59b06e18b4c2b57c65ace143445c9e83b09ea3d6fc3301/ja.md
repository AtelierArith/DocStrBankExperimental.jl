```
plyapdi(A, E, B; cyclic, abstol, reltol, maxiter, nshifts, shifts, loginf) -> (U, info)
plyapdi(A, B; cyclic, abstol, reltol, maxiter, nshifts, shifts, loginf) -> (U, info)
```

一般化離散リャプノフ方程式の解 `X = UU'` の低ランク因子 `U` を計算します。

```
  AXA' - EXE' + BB' = 0,
```

ここで `A` と `E` は正方行列で、`B` は `A` と同じ行数を持つ実行列です。ペンシル `A - λE` は、絶対値が1未満の固有値のみを持つ必要があります。2回目の呼び出しでは `E = I` が仮定されています。

名前付きタプル `info` には、LR-ADIアルゴリズムの実行に関連する情報が含まれています。具体的には、`info.niter` には実行された反復回数が含まれ、`info.res_fact` には残差因子のノルムが含まれ、`info.res` には `loginf = true` の場合、初期近似のノルムに対して正規化された残差ノルムのベクトルが含まれます。`info.rc` には、`loginf = true` の場合、解の構築における相対変化のノルムのベクトルが含まれ、`info.used_shift` には使用されたシフトのベクトルが含まれます。

キーワード引数 `abstol`（デフォルト: `abstol = 1e-12`）は、正規化された残差に対する収束テストに使用される許容誤差であり、キーワード引数 `reltol`（デフォルト: `reltol = 0`）は解の相対変化に対する許容誤差です。キーワード引数 `maxiter` は、最大反復回数を設定するために使用できます（デフォルト: `maxiter = 100`）。キーワード引数 `nshifts` は、反復サイクルで使用するシフトの希望数を指定します（デフォルト: `nshifts = 6`）。キーワード引数 `shifts` は、反復を開始するために使用される事前計算された複素共役シフトのセットを提供するために使用できます（デフォルト: `shifts = missing`）。キーワード引数 `loginf = true` を使用すると、正規化された残差値と解の増分のノルムを結果の情報構造に出力として保存できます（デフォルト: `loginf = false`）。

[1] で提案された強化を伴う低ランクADI（LR-ADI）法は、[2] で説明されたフリーソフトウェアのMATLABコードに触発されて、離散ケースに適応されています。`cyclic = true` の場合、キーワード引数 `shifts` で提供された事前計算されたシフトを使用して、[3] の循環低ランク法が適応されます。

*参考文献*

[1] P. Kürschner. Efficient Low-Rank Solution of Large-Scale Matrix Equations.      Dissertation, Otto-von-Guericke-Universität, Magdeburg, Germany, 2016. Shaker Verlag,

[2] P. Benner, M. Köhler, and J. Saak. “Matrix Equations, Sparse Solvers: M-M.E.S.S.-2.0.1—     Philosophy, Features, and Application for (Parametric) Model Order Reduction.”      In Model Reduction of Complex Dynamical Systems, Eds. P. Benner et.al., 171:369–92, Springer, 2021.

[3] T. Penzl, A cyclic low-rank Smith method for large sparse Lyapunov equations,      SIAM J. Sci. Comput. 21 (4) (1999) 1401–1418.
