```
 tvstm(A, tf, t0; solver, reltol, abstol, dt) -> Φ
```

周期的時間変化係数を持つ線形常微分方程式の状態遷移行列を計算します。与えられた正方形の周期的連続時間行列 `A(t)`、初期時間 `t0` および最終時間 `tf` に対して、状態遷移行列 `Φ(tf,t0)` は、次の均質線形常微分方程式を数値的に積分することによって計算されます。

```
  dΦ(t,t0)/dt = A(t)Φ(t,t0),  Φ(t0,t0) = I
```

時間区間 `[t0,tf]` で。 `A` は [`PeriodicFunctionMatrix`](@ref)、[`HarmonicArray`](@ref)、[`PeriodicSymbolicMatrix`](@ref) または [`FourierFunctionMatrix`](@ref) として与えられる場合があります。

使用するODEソルバーは、キーワード引数 `solver` を使用して指定できます（以下を参照）、必要な相対精度 `reltol`（デフォルト: `reltol = 1.e-3`）、絶対精度 `abstol`（デフォルト: `abstol = 1.e-7`）および/または固定ステップ長 `dt`（デフォルト: `dt = tf-t0`）とともに指定できます。希望する相対精度 `reltol` に応じて、`reltol >= 1.e-4` の場合は低次のソルバーが使用され、一般的に非常に効率的ですが、精度は低くなります。`reltol < 1.e-4` の場合は、高精度の要求に対応できる高次のソルバーが使用されます。

次のソルバーは [OrdinaryDiffEq.jl](https://github.com/SciML/OrdinaryDiffEq.jl) パッケージから選択できます：

`solver = "non-stiff"` - 非剛性問題用のソルバーを使用します（`Tsit5()` または `Vern9()`）;

`solver = "stiff"` - 剛性問題用のソルバーを使用します（`Rodas4()` または `KenCarp58()`）;

`solver = "linear"` - 固定時間ステップ `dt` を持つ線形ODE用の特別なソルバーを使用します（`MagnusGL6()`）;

`solver = "symplectic"` - シンプレクティックハミルトニアン構造を保持するソルバーを使用します（`IRKGL16()`）;

`solver = "auto"` - デフォルトのソルバーを使用し、剛性問題を自動的に検出します（`AutoTsit5(Rosenbrock23())` または `AutoVern9(Rodas5())`）。 
