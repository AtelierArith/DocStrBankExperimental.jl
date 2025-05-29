```
pcric(A, R, Q; K = 10, N = 1, adj = false, solver, reltol, abstol, fast, intpol, dt) -> (X, EVALS)
```

周期リカッティ微分方程式を解く

```
.                                                 
X(t) = A(t)X(t) + X(t)A(t)' + Q(t) - X(t)R(t)X(t) ,  adj = false の場合、
```

または 

```
 .                                                
-X(t) = A(t)'X(t) + X(t)A(t) + Q(t) - X(t)R(t)X(t) , adj = true の場合
```

そして、安定した閉ループ特性乗数を `EVALS` に計算します（詳細は [`pgcric`](@ref) を参照）。

周期行列 `A`、`R` および `Q` は同じ型、同じ次元、同じ周期を持ち、さらに `R` と `Q` は対称でなければなりません。結果として得られる対称周期解 `X` は `PeriodicFunctionMatrix` 型を持ち、`X(t)` を使用して時刻 `t` における `X` の値を評価できます。`X` の周期は `A`、`R` および `Q` の最小公倍数の周期に設定され、サブ周期の数はそれに応じて調整されます。 *注意:* 現在、`PeriodicTimeSeriesMatrix` および `PeriodicSwitchingMatrix` 型はサポートされていません。

`fast = true`（デフォルト）の場合、複数発射法が高速ペンシル削減技術と組み合わせて使用され、周期解が `t = 0` で決定され、適切な周期微分リカッティ方程式の複数点生成器が決定されます（詳細は [1] を参照）。 `fast = false` の場合、複数発射法が周期シュール分解と組み合わせて使用され、適切なシンプレクティック遷移行列の安定した周期不変部分空間から直接複数点生成器が決定されます（詳細は [2] を参照）。

複数点周期生成器の決定には、[IRKGaussLegendre.jl](https://github.com/SciML/IRKGaussLegendre.jl) パッケージからの暗黙的ルンゲ-クッタ ガウス-ルジャンドル 16 次法が使用され、適切なハミルトン系を統合します [2]。

補間またはODE統合による解の評価には、[OrdinaryDiffEq.jl](https://github.com/SciML/OrdinaryDiffEq.jl) パッケージから以下のソルバーをキーワード引数 `solver` を使用して選択できます：

`solver = "non-stiff"` - 非剛性問題用のソルバーを使用（`Tsit5()` または `Vern9()`）;

`solver = "stiff"` - 剛性問題用のソルバーを使用（`Rodas4()` または `KenCarp58()`）;

`solver = "auto"` - デフォルトのソルバーを使用し、剛性問題を自動的に検出します（`AutoTsit5(Rosenbrock23())` または `AutoVern9(Rodas5())`）。

計算された解の精度は、相対精度キーワード `reltol`（デフォルト: `reltol = 1.e-4`）および絶対精度キーワード `abstol`（デフォルト: `abstol = 1.e-7`）を介して制御できます。希望する相対精度 `reltol` に応じて、`reltol >= 1.e-4` の場合は低次のソルバーが使用され、一般的に非常に効率的ですが、精度は低くなります。`reltol < 1.e-4` の場合は、高精度の要求に対応できる高次のソルバーが使用されます。

大きな値の `K` に対しては、並列計算を使用して離散時間問題の行列または複数ドメイン補間に基づく解を決定できます。これには、複数の実行スレッドでJuliaを起動する必要があります。実行スレッドの数は、`-t/--threads` コマンドライン引数を使用するか、`JULIA_NUM_THREADS` 環境変数を使用して制御されます。

*参考文献*

[1] A. Varga. 周期的な微分行列方程式の解法と周期システムノルム計算への応用。Proc. IEEE CDC/ECC, Seville, 2005。

[2] A. Varga. 周期的リカッティ方程式の解法。Numerical Linear Algebra with Applications, 15:809-835, 2008。
