```
pgcric(A, R, Q[, K = 1]; adj = false, solver, reltol, abstol, fast, PSD_SLICOT) -> (X, EVALS)
```

周期リカッティ微分方程式の*フィルタリング*形式の周期生成器を計算します。

```
.                                                  
X(t) = A(t)X(t) + X(t)A(t)' + Q(t) - X(t)R(t)X(t), もし adj = false の場合、
```

または*制御*形式で

```
 .                                              
-X(t) = A(t)'X(t) + X(t)A(t) + Q(t) - X(t)R(t)X(t) , もし adj = true の場合、
```

ここで `A(t)`, `R(t)` および `Q(t)` は同じ周期を持つ周期行列であり、`A(t)` は正方行列、`R(t)` は対称かつ正定値、`Q(t)` は対称かつ正半定値です。結果として得られる `X` は、`N` 成分を持つ周期的生成行列のコレクションであり、`A(t)`, `R(t)` および `Q(t)` が定数行列である場合は `N = 1`、それ以外の場合は `N = K` です。`EVALS` には、対応するハミルトン行列のモノドロミー行列の安定特性乗数（閉ループ特性乗数とも呼ばれる）が含まれます。`X` の周期は `A(t)`, `R(t)` および `Q(t)` の最小公倍数の周期に設定され、サブ周期の数はそれに応じて調整されます。`X` の任意の成分行列は、適切な微分方程式を統合することによって完全な周期にわたって解を生成するために使用される有効な初期値です。

`fast = true`（デフォルト）の場合、複数の射撃法が高速ペンシル削減技術と組み合わせて使用され、`t = 0` での周期解を決定し、適切な周期微分リカッティ方程式の複数点生成器が決定されます（詳細については [2] を参照）。`fast = false` の場合、複数の射撃法が周期シュル分解と組み合わせて使用され、適切なシンプレクティック遷移行列の安定周期不変部分空間から直接複数点生成器が決定されます（詳細については [2] も参照）。

適切なハミルトン系を統合するために推奨されるソルバー [2] は、[IRKGaussLegendre.jl](https://github.com/SciML/IRKGaussLegendre.jl) パッケージの暗黙的ルンゲ-クッタ ガウス-ルジャンドル 16 次法であり、`solver = "symplectic"`（デフォルト）で選択できます。

[OrdinaryDiffEq.jl](https://github.com/SciML/OrdinaryDiffEq.jl) パッケージの他のODEソルバーも選択できます：

`solver = "non-stiff"` - 非剛性問題用のソルバーを使用します（`Tsit5()` または `Vern9()`）;

`solver = "stiff"` - 剛性問題用のソルバーを使用します（`Rodas4()` または `KenCarp58()`）;

`solver = "linear"` - 固定時間ステップ `dt` を持つ線形ODE用の特別なソルバーを使用します（`MagnusGL6()`）;

`solver = "auto"` - デフォルトのソルバーを使用し、剛性問題を自動的に検出します（`AutoTsit5(Rosenbrock23())` または `AutoVern9(Rodas5())`）。

計算された解の精度は、相対精度キーワード `reltol`（デフォルト: `reltol = 1.e-4`）および絶対精度キーワード `abstol`（デフォルト: `abstol = 1.e-7`）を介して制御できます。望ましい相対精度 `reltol` に応じて、`reltol >= 1.e-4` の場合は低次のソルバーが使用され、一般的に非常に効率的ですが、精度は低くなります。`reltol < 1.e-4` の場合は、高精度の要求に対応できる高次のソルバーが使用されます。

大きな値の `K` に対しては、複数の実行スレッドでJuliaを起動することにより、離散時間問題の行列の並列計算を代わりに実行できます。実行スレッドの数は、`-t/--threads` コマンドライン引数を使用するか、`JULIA_NUM_THREADS` 環境変数を使用して制御されます。

*参考文献*

[1] A. Varga. 周期的システムノルム計算への応用を伴う周期的微分行列方程式の解法について。Proc. IEEE CDC/ECC, Seville, 2005.

[2] A. Varga. 周期的リカッティ方程式の解法について。Numerical Linear Algebra with Applications, 15:809-835, 2008.
