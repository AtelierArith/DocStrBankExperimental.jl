```
pfcric(A, C, R, Q; K = 10, N = 1, solver, intpol, reltol, abstol, fast) -> (X, EVALS, F)
```

周期的フィルタリングに関連するリカッティ微分方程式の対称安定解 `X(t)` を計算します。

```
.                                                 -1 
X(t) = A(t)X(t) + X(t)A(t)' + Q(t) - X(t)C(t)'R(t)  C(t)X(t) ,
```

周期的安定カルマンゲイン 

```
                    -1
F(t) = X(t)C(t)'R(t)
```

および `A(t)-F(t)C(t)` の対応する安定特性乗数 `EVALS` を求めます。

周期行列 `A`、`C`、`R` および `Q` は同じ型であり、同じ周期を持つ必要があり、さらに `R` は対称正定値であり、`Q` は対称半正定値でなければなりません。得られた対称周期解 `X` の型は `PeriodicFunctionMatrix` であり、`X(t)` を使用して時刻 `t` における `X` の値を評価できます。`X` は `A`、`C`、`R` および `Q` の最小公倍数の周期に設定され、サブ周期の数はそれに応じて調整されます。

`fast = true`（デフォルト）の場合、複数射撃法が高速ペンシル削減技術と組み合わせて使用され、`t = 0` における周期解を決定し、適切な周期微分リカッティ方程式の複数点生成器が決定されます（詳細は [2] を参照）。`fast = false` の場合、複数射撃法が周期シュール分解と組み合わせて使用され、適切なシンプレクティック遷移行列の安定周期不変部分空間から直接複数点生成器が決定されます（詳細は [2] も参照）。

キーワード引数 `K` は、得られる複数点周期生成器に使用されるグリッドポイントの数を指定します（デフォルト: `K = 10`）。得られた周期生成器は最終的に周期関数行列に変換され、与えられた `t` に対して関数値 `X(t)` を決定します。`intpol = true`（デフォルト）の場合は適切な微分方程式の解を補間し、`intpol = false` の場合は最寄りのグリッドポイント値から適切なODEを統合します。補間ベースの評価のために、整数キーワード引数 `N` を使用して統合領域（すなわち1周期）を `N` のサブドメインに分割し、各ドメインで補間を別々に行うことができます。`N` のデフォルト値は `N = 1` です。

複数点周期生成器の決定には、[IRKGaussLegendre.jl](https://github.com/SciML/IRKGaussLegendre.jl) パッケージからの暗黙的ルンゲクッタガウス・ルジャンドル16次法が使用され、適切なハミルトニアン系を統合します [2]。

補間またはODE統合による解の評価のために、次のソルバーが [OrdinaryDiffEq.jl](https://github.com/SciML/OrdinaryDiffEq.jl) パッケージから選択できます。キーワード引数 `solver` を使用します：

`solver = "non-stiff"` - 非剛性問題用のソルバーを使用します（`Tsit5()` または `Vern9()`）;

`solver = "stiff"` - 剛性問題用のソルバーを使用します（`Rodas4()` または `KenCarp58()`）;

`solver = "auto"` - デフォルトのソルバーを使用し、剛性問題を自動的に検出します（`AutoTsit5(Rosenbrock23())` または `AutoVern9(Rodas5())`）。

計算された解の精度は、相対精度キーワード `reltol`（デフォルト: `reltol = 1.e-4`）および絶対精度キーワード `abstol`（デフォルト: `abstol = 1.e-7`）を介して制御できます。希望する相対精度 `reltol` に応じて、`reltol >= 1.e-4` の場合は低次のソルバーが使用され、一般的に非常に効率的ですが、精度は低くなります。`reltol < 1.e-4` の場合は、高精度要求に対応できる高次のソルバーが使用されます。

`K` の大きな値に対しては、Juliaを複数の実行スレッドで起動することにより、離散時間問題の行列の並列計算を代替的に実行できます。実行スレッドの数は、`-t/--threads` コマンドライン引数を使用するか、`JULIA_NUM_THREADS` 環境変数を使用して制御されます。

*参考文献*

[1] A. Varga. On solving periodic differential matrix equations with applications to periodic system norms computation.      Proc. IEEE CDC/ECC, Seville, 2005. 

[2] A. Varga. On solving periodic Riccati equations.       Numerical Linear Algebra with Applications, 15:809-835, 2008.    
