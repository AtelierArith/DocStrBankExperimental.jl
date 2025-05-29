```
psh2norm(psys, K; adj = false, smarg = 1, fast = false, offset = sqrt(ϵ), solver = "auto", reltol = 1.e-4, abstol = 1.e-7, quad = false) -> nrm
```

連続時間周期システム `psys = (A(t),B(t),C(t),D(t))` の H2-ノルムを計算します。ノルムの計算には、[1] に示された式が使用され、`K` の離散化点を用いた [2] のマルチシューティングアプローチと組み合わせられます。周期 `T` の周期システムに対して、`adj = false` の場合、ノルムは次のように計算されます。

```
 nrm = sqrt(Integral(tr(C(t)P(t)C(t)')))dt/T),
```

ここで `P(t)` は、周期的微分リャプノフ方程式を満たす制御可能性グラミアンです。

```
 .
 P(t) = A(t)P(t)A(t)' + B(t)B(t)',
```

一方、`adj = true` の場合、ノルムは次のように計算されます。

```
nrm = sqrt(Integral(tr(B(t)'Q(t)B(t)))dt/T),
```

ここで Q(t) は、周期的微分リャプノフ方程式を満たす可観測性グラミアンです。

```
 .
-Q(t) = A(t)'Q(t)A(t) + C(t)'C(t) .
```

`quad = true` の場合、時間値の合計に基づく単純な数値積分公式が使用されます（[2] を参照）。このオプションは、より高速な評価を保証しますが、`quad = false`（デフォルト）の場合に使用される正確な評価よりも精度が低い可能性があります。

不安定なシステムや非ゼロの `D(t)` に対しては、ノルムは無限大に設定されます。

安定性を評価するために、`A(t)` の特性乗数の絶対値は `smarg-β` より小さくなければなりません。ここで `smarg` は離散時間安定性マージン（デフォルト: `smarg = 1`）であり、`β` は固有値の安定性を数値的に評価するためにキーワードパラメータ `offset = β` を介して指定されます。`β` に使用されるデフォルト値は `sqrt(ϵ)` であり、`ϵ` は作業機械精度です。`fast = false`（デフォルト）の場合、安定性は `A(t)` の周期的シュール分解に基づくアプローチを使用してチェックされますが、`fast = true` の場合はリフティングベースのアプローチを使用して安定性がチェックされます。

連続時間問題を離散時間問題に変換するために使用される ODE ソルバーは、キーワード引数 `solver` を使用して指定でき、必要な相対精度 `reltol`（デフォルト: `reltol = 1.e-4`）および絶対精度 `abstol`（デフォルト: `abstol = 1.e-7`）とともに指定されます。希望する相対精度 `reltol` に応じて、`reltol >= 1.e-4` の場合は低次のソルバーが使用され、一般的に非常に効率的ですが、精度は低くなります。`reltol < 1.e-4` の場合は、高精度の要求に対応できる高次のソルバーが使用されます。

次のソルバーは [OrdinaryDiffEq.jl](https://github.com/SciML/OrdinaryDiffEq.jl) パッケージから選択できます。

`solver = "non-stiff"` - 非剛性問題用のソルバーを使用します（`Tsit5()` または `Vern9()`）;

`solver = "stiff"` - 剛性問題用のソルバーを使用します（`Rodas4()` または `KenCarp58()`）;

`solver = "auto"` - 剛性問題を自動的に検出するデフォルトのソルバーを使用します（`AutoTsit5(Rosenbrock23())` または `AutoVern9(Rodas5()`）。 

*参考文献*

[1] P. Colaneri. Continuous-time periodic systems in H2 and H∞: Part I: Theoretical Aspects.     Kybernetika, 36:211-242, 2000. 

[2] A. Varga, On solving periodic differential matrix equations with applications to periodic system norms computation.     Proc. CDC/ECC, Seville, p.6545-6550, 2005.  
