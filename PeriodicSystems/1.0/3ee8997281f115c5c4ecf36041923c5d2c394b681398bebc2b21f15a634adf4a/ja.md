```
pstimeresp(sys, u, t, x0 = zeros(sys.nx); state_history = false, solver, reltol, abstol) -> (y, tout, x)
```

連続時間周期システム `sys = (A(t),B(t),C(t),D(t))` の時間応答を、入力信号 `u` と `t` に基づいて計算します。時間ベクトル `t` は、定期的に間隔を空けた時間サンプルで構成されています。入力 `u` は、`sys` の入力数と同じ数の成分を持つ時間依存信号のベクトルとして指定されます。ベクトル `x0` は、時間 `t[1]` における初期状態ベクトルを指定し、省略した場合はゼロに設定されます。

行列 `y` には、`sys` の出力の結果としての時間履歴が含まれ、ベクトル `tout` には対応する時間サンプルの値が含まれます。`y` の `i` 行目には、時間 `tout[i]` における出力値が含まれます。キーワードパラメータ `state_history = true` が使用されると、行列 `x` には状態ベクトルの結果としての時間履歴が含まれ、その `i` 行目には時間 `tout[i]` における状態値が含まれます。デフォルトでは、状態履歴は計算されず、`x = nothing` となります。

使用するODEソルバーは、キーワード引数 `solver` を使用して指定できます（以下を参照）、必要な相対精度 `reltol`（デフォルト: `reltol = 1.e-4`）、絶対精度 `abstol`（デフォルト: `abstol = 1.e-7`）、および固定ステップ長 `dt`（デフォルト: `dt = 0`）とともに指定され、`solver = "symplectic"` の場合のみ使用されます。望ましい相対精度 `reltol` に応じて、`reltol >= 1.e-4` の場合は低次のソルバーが使用され、一般的に非常に効率的ですが、精度は低くなります。`reltol < 1.e-4` の場合は、高精度の要求に対応できる高次のソルバーが使用されます。

以下のソルバーは、[OrdinaryDiffEq.jl](https://github.com/SciML/OrdinaryDiffEq.jl) パッケージから選択できます：

`solver = "non-stiff"` - 非剛性問題用のソルバーを使用します（`Tsit5()` または `Vern9()`）;

`solver = "stiff"` - 剛性問題用のソルバーを使用します（`Rodas4()` または `KenCarp58()`）;

`solver = "linear"` - 固定時間ステップ `dt` を持つ線形ODE用の特別なソルバーを使用します（`MagnusGL6()`）;

`solver = "symplectic"` - シンプレクティックハミルトニアン構造を保持するソルバーを使用します（`IRKGL16()`）;

`solver = "auto"` - デフォルトのソルバーを使用し、剛性問題を自動的に検出します（`AutoTsit5(Rosenbrock23())` または `AutoVern9(Rodas5()`）。
