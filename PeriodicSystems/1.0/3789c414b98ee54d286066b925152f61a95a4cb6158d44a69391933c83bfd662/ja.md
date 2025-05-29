```
 psc2d([PMT,] psysc, Ts; solver, reltol, abstol, dt) -> psys::PeriodicStateSpace{PMT}
```

周期 `T` の連続時間周期システム `psysc = (A(t),B(t),C(t),D(t))` とサンプリング時間 `Ts` に対して、ゼロオーダーホールドに基づく離散化手法を用いて対応する離散周期システム `psys = (Ad,Bd,Cd,Dd)` を計算します。結果として得られる離散化システム `psys` は、デフォルトで `PeriodicArray` 型の行列を持つか、または `PMT` 型の行列を持ちます。ここで `PMT` は `PeriodicMatrix`、`PeriodicArray`、`SwitchingPeriodicMatrix` または `SwitchingPeriodicArray` のいずれかの型です。

離散化は、拡張状態空間行列 `[A(t) B(t); 0 0]` の `K = T/Ts` 状態遷移行列の積としてモノドロミー行列を決定することによって行われ、対応する同次線形常微分方程式を数値的に統合します。使用するODEソルバーは、キーワード引数 `solver` を使用して指定でき、必要な相対精度 `reltol`（デフォルト: `reltol = 1.e-3`）、絶対精度 `abstol`（デフォルト: `abstol = 1.e-7`）および/または固定ステップ長 `dt`（デフォルト: `dt = Ts/10`）を指定します。望ましい相対精度 `reltol` に応じて、`reltol >= 1.e-4` の場合は低次のソルバーが使用され、一般的に非常に効率的ですが、精度は低くなります。`reltol < 1.e-4` の場合は、高精度の要求に対応できる高次のソルバーが使用されます。

次のソルバーは、[OrdinaryDiffEq.jl](https://github.com/SciML/OrdinaryDiffEq.jl) パッケージから選択できます：

`solver = "non-stiff"` - 非剛性問題用のソルバーを使用します（`Tsit5()` または `Vern9()`）;

`solver = "stiff"` - 剛性問題用のソルバーを使用します（`Rodas4()` または `KenCarp58()`）;

`solver = "linear"` - 固定時間ステップ `dt` を持つ線形ODE用の特別なソルバーを使用します（`MagnusGL6()`）;

`solver = "symplectic"` - シンプレクティックハミルトニアン構造を保持するソルバーを使用します（`IRKGL16()`）;

`solver = ""` - デフォルトのソルバーを使用し、剛性問題を自動的に検出します（`AutoTsit5(Rosenbrock23())` または `AutoVern9(Rodas5())`）。

大きな値の `K` に対しては、複数の実行スレッドでJuliaを起動することにより、因子の並列計算を代替的に行うことができます。実行スレッドの数は、`-t/--threads` コマンドライン引数を使用するか、`JULIA_NUM_THREADS` 環境変数を使用して制御されます。
