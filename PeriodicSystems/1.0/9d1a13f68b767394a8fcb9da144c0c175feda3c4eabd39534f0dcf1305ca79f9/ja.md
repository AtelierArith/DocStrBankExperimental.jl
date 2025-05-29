```
pshanorm(psys, K; smarg = 1, offset = sqrt(ϵ), solver = "auto", reltol = 1.e-4, abstol = 1.e-7) -> nrm
```

安定な連続時間周期システム `psys = (A(t),B(t),C(t),D(t))` のハンケルノルムを計算します。ノルムの計算には、[1] で提案されたアプローチが、`K` 個の離散化点を使用したマルチシューティングアプローチと組み合わせて使用されます。周期 `T` の周期システムに対して、ハンケルノルムは次のように定義されます。

```
 nrm = sqrt(max(Λ(P(t)Q(t)))), for t ∈ [0,T]
```

ここで `P(t)` は、周期的微分リャプノフ方程式を満たす制御可能性グラミアンです。

```
 .
 P(t) = A(t)P(t)A(t)' + B(t)B(t)',
```

`Q(t)` は、周期的微分リャプノフ方程式を満たす可観測性グラミアンです。

```
 .
-Q(t) = A(t)'Q(t)A(t) + C(t)'C(t) .
```

ノルムは、区間 `[0,T]` の `P(t)` と `Q(t)` の `K` 時間値から評価され、精度は通常 `K` の値が大きいほど良くなります。

安定性を評価するために、`A(t)` の特性乗数の絶対値は `smarg-β` より小さくなければなりません。ここで `smarg` は離散時間安定性マージン（デフォルト: `smarg = 1`）であり、`β` は固有値の安定性を数値的に評価するためにキーワードパラメータ `offset = β` を介して指定されるオフセットです。`β` に使用されるデフォルト値は `sqrt(ϵ)` であり、`ϵ` は作業用の機械精度です。

連続時間の問題を離散時間の問題に変換するために使用されるODEソルバーは、キーワード引数 `solver` を使用して指定でき、必要な相対精度 `reltol`（デフォルト: `reltol = 1.e-4`）および絶対精度 `abstol`（デフォルト: `abstol = 1.e-7`）とともに指定されます。希望する相対精度 `reltol` に応じて、`reltol >= 1.e-4` の場合は低次のソルバーが使用され、一般的に非常に効率的ですが、精度は低くなります。`reltol < 1.e-4` の場合は、高精度の要求に対応できる高次のソルバーが使用されます。

次のソルバーは、[OrdinaryDiffEq.jl](https://github.com/SciML/OrdinaryDiffEq.jl) パッケージから選択できます。

`solver = "non-stiff"` - 非剛性問題用のソルバーを使用します（`Tsit5()` または `Vern9()`）;

`solver = "stiff"` - 剛性問題用のソルバーを使用します（`Rodas4()` または `KenCarp58()`）;

`solver = "auto"` - デフォルトのソルバーを使用し、剛性問題を自動的に検出します（`AutoTsit5(Rosenbrock23())` または `AutoVern9(Rodas5()`）。 

*参考文献*

[1] A. Varga, On solving periodic differential matrix equations with applications to periodic system norms computation.     Proc. CDC/ECC, Seville, p.6545-6550, 2005.  
