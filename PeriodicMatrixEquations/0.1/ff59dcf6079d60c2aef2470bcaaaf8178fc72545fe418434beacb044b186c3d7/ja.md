```
pgclyap2(A, C::AbstractMatrix, E, [, K = 1]; solver, reltol, abstol) -> (X,Y)
```

離散時間周期リャプノフ方程式の解を計算します。

```
X(i+1) = Φ(i)*X(i)*Φ'(i) + W(i), i = 1, ..., K, X(K+1) := X(1)
```

および周期リャプノフ微分方程式の周期生成器を計算します。

```
 .
-Y(t) = A(t)'Y(t) + Y(t)A(t) + E(t).
```

周期行列 `A` と `E` および定数行列 `C` は同じ次元を持たなければならず、`A` と `E` は同じ型で、共通の周期を持たなければなりません。さらに、`C` と `E` は対称でなければなりません。 `Φ(i)` は、`A` に対応する時間間隔 `[Δ*(i-1), Δ*i]` 上の遷移行列を示し、ここで `Δ = T/K` で、`T` は `A` と `E` の共通周期です。 `W(i) = 0` は `i = 1, ..., K-1` の場合であり、`W(K) = C` です。 `A` と `E` が `PeriodicFunctionMatrix`、`HarmonicArray`、`FourierFunctionMatrix` または `PeriodicSymbolicMatrix` の型を持つ場合、結果として得られる `Y` は、`N` 成分を持つ周期的生成行列のコレクションであり、`A` と `E` が定数行列である場合は `N = 1`、それ以外の場合は `N = K` です。 `Y` の周期 `T` は `A` と `E` の最小公倍数の共通周期に設定され、サブ周期の数はそれに応じて調整されます。 `Y` の任意の成分行列は、適切な微分方程式を統合することによって完全な周期にわたって解を生成するために使用される有効な初期値です。 [1] の多重射撃法が最初に使用され、連続時間周期リャプノフを離散時間周期リャプノフ方程式に変換し、次に適切な離散時間周期リャプノフ方程式を解くことによって生成器解を計算します。この解法は [2] の周期シュール法を使用します。

連続時間の問題を離散時間の問題に変換するために使用されるODEソルバーは、キーワード引数 `solver` を使用して指定でき、必要な相対精度 `reltol`（デフォルト: `reltol = 1.e-4`）および絶対精度 `abstol`（デフォルト: `abstol = 1.e-7`）とともに指定されます。希望する相対精度 `reltol` に応じて、`reltol >= 1.e-4` の場合は低次のソルバーが使用され、一般的に非常に効率的ですが、精度は低くなります。 `reltol < 1.e-4` の場合は、高精度の要求に対応できる高次のソルバーが使用されます。

次のソルバーは [OrdinaryDiffEq.jl](https://github.com/SciML/OrdinaryDiffEq.jl) パッケージから選択できます。

`solver = "non-stiff"` - 非剛性問題用のソルバーを使用します（`Tsit5()` または `Vern9()`）;

`solver = "stiff"` - 剛性問題用のソルバーを使用します（`Rodas4()` または `KenCarp58()`）;

`solver = "auto"` - デフォルトのソルバーを使用し、剛性問題を自動的に検出します（`AutoTsit5(Rosenbrock23())` または `AutoVern9(Rodas5()`）。 

離散時間問題の行列の並列計算は、複数の実行スレッドでJuliaを起動することによって代わりに実行できます。実行スレッドの数は、`-t/--threads` コマンドライン引数を使用するか、`JULIA_NUM_THREADS` 環境変数を使用して制御されます。

*参考文献*

[1] A. Varga. 周期的な微分行列方程式の解法と周期的システムノルム計算への応用。 Proc. IEEE CDC/ECC, Seville, 2005.

[2] A. Varga. 周期リャプノフ方程式: 一部の応用と新しいアルゴリズム。 Int. J. Control, vol, 67, pp, 69-87, 1997.  
