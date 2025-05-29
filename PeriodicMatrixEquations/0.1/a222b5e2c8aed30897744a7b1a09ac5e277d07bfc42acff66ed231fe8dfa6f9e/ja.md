```
pcplyap(A, C; K = 10, adj = false, solver, reltol, abstol) -> U
```

周期的リャプノフ微分方程式の解 `X(t) = U(t)U(t)'` の上三角周期因子 `U(t)` を計算します。

```
.
X(t) = A(t)X(t) + X(t)A(t)' + C(t)C(t)' , if adj = false,
```

または、周期的リャプノフ微分方程式の解 `X(t) = U(t)'U(t)` の上三角周期因子 `U(t)` を計算します。

```
 .
-X(t) = A(t)'X(t) + X(t)A(t) + C(t)'C(t) , if adj = true.
```

周期行列 `A` と `C` は同じ型で、共通の周期を持ち、`A` は安定でなければなりません。結果として得られる上三角周期因子 `U` は `PeriodicFunctionMatrix` 型であり、`U(t)` を使用して時刻 `t` における `U` の値を評価できます。`U` の周期は `A` と `C` の最小公倍数の共通周期に設定され、サブ周期の数はそれに応じて調整されます。

[1] の多重射撃法の拡張が使用され、（連続時間の）周期的リャプノフ方程式を解の多点生成器が満たす離散時間の周期的リャプノフ方程式に変換します。キーワード引数 `K` は、連続時間の問題の離散化に使用されるグリッドポイントの数を指定します（デフォルト: `K = 10`）。多点生成器の上三角因子は、適切な離散時間の周期的リャプノフ方程式を解くことによって計算され、反復法（アルゴリズム 5）を使用します [2]。得られた周期的生成器は、最寄りのグリッドポイント値から適切なODEを統合することによって、与えられた `t` に対する関数値 `U(t)` を決定する周期関数行列に最終的に変換されます。

連続時間の問題を離散時間の問題に変換するために使用されるODEソルバーは、キーワード引数 `solver` を使用して指定でき、必要な相対精度 `reltol`（デフォルト: `reltol = 1.e-4`）および絶対精度 `abstol`（デフォルト: `abstol = 1.e-7`）とともに指定されます。希望する相対精度 `reltol` に応じて、`reltol >= 1.e-4` の場合は低次のソルバーが使用され、一般的に非常に効率的ですが、精度は低くなります。`reltol < 1.e-4` の場合は、高精度の要求に対応できる高次のソルバーが使用されます。

次のソルバーは、[OrdinaryDiffEq.jl](https://github.com/SciML/OrdinaryDiffEq.jl) パッケージから選択できます：

`solver = "non-stiff"` - 非剛性問題用のソルバーを使用します（`Tsit5()` または `Vern9()`）;

`solver = "stiff"` - 剛性問題用のソルバーを使用します（`Rodas4()` または `KenCarp58()`）;

`solver = "auto"` - 剛性問題を自動的に検出するデフォルトのソルバーを使用します（`AutoTsit5(Rosenbrock23())` または `AutoVern9(Rodas5())`）。

関数評価を高速化するために、キーワード引数 `intpol = true`（デフォルト: `intpol = true`）を設定することで、補間に基づく関数評価を使用できます。`A` と `C` が `PeriodicSwitchingMatrix` 型の場合、補間は不可能です。

離散時間の問題の行列の並列計算は、複数の実行スレッドでJuliaを起動することによって代わりに実行できます。実行スレッドの数は、`-t/--threads` コマンドライン引数を使用するか、`JULIA_NUM_THREADS` 環境変数を使用して制御されます。

*参考文献*

[1] A. Varga. On solving periodic differential matrix equations with applications to periodic system norms computation. Proc. IEEE CDC/ECC, Seville, 2005.

[2] A. Varga. Periodic Lyapunov equations: some applications and new algorithms. Int. J. Control, vol, 67, pp, 69-87, 1997.
