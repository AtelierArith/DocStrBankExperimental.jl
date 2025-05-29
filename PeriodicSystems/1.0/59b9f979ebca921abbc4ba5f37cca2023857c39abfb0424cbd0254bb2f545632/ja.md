```
pdlqofc(psys, Q, R; S, G = I, sdeg = 1, stabilizer, optimizer, vinit, maxiter, vtol, Jtol, gtol, show_trace) -> (Fopt, info)
```

離散時間周期状態空間システム `psys = (A(t),B(t),C(t),D(t))` の最適周期フィードバックゲイン `Fopt(t)` を計算します。このシステムは次の形式を持ちます。

```
x(t+1) = A(t)x(t) + B(t)u(t) + Bw(t)w(t) 
  y(t) = C(t)x(t) + D(t)u(t) + Dw(t)w(t) ,
```

出力フィードバック制御則において、期待値の二次指標を最小化するための

```
 J = E{ Sum [x(t)'*Q(t)*x(t) + 2*x(t)'*S(t)*u(t) + u(t)'*R(t)*u(t)] },
```

ここで `Q(t)`, `R(t)` および `S(t)` は周期的重み行列です。制御入力 `u(t)` の次元 `m` と測定可能な出力 `y(t)` の次元 `p` を持つ `n` 次のシステムに対して、`Q(t)` と `R(t)` はそれぞれ `n×n` および `m×m` の対称周期行列であり、`S(t)` は `n×m` の周期行列で、キーワード引数 `S` を介して指定できます。デフォルトでは `S = missing` であり、この場合 `S(t) = 0` と仮定されます。周期行列 `Q(t)`,`R(t)` および `S(t)` は状態空間システムの行列と同じ型であり、すなわち `PeriodicMatrix` または `PeriodicArray` のいずれかです。`u(t)` の次元 `m` は `R(t)` の次元から推測されます。`Q`, `R` および `S` は定数実行列としても提供できます。

得られる `m×p` の周期出力フィードバックゲイン `Fopt(t)` は状態空間システム行列と同じ型を持ち、次のように計算されます。`Fopt(t) = inv(I+F(t)D(t))*F(t)` で、`F(t)` は次のように定義されます。

```
 F(t) = F_i  for i ∈ {1, ..., ns}
```

ここで `ns` は周期内のサンプリング時間の数（すなわち `ns = psys.period/psys.Ts`）であり、`F_i` は `i` 番目のゲインです。

初期状態 `x(0)` の共分散はキーワード引数 `G` を介して指定できます（デフォルト: `G = I`）。閉ループ特性の固有値の望ましい安定度はキーワード引数 `sdeg` を使用して指定できます（デフォルト: `sdeg = 1`）。

最適フィードバックゲイン `F_i` を `i = 1, ...., ns` のために決定するために、最適化パッケージ [`Optim.jl`](https://github.com/JuliaNLSolvers/Optim.jl) にあるツールを使用した最適化ベースのアプローチが採用されます。デフォルトでは、制約のない最小化のために勾配ベースの制限付きメモリ準ニュートン法（`L-BFGS` とも呼ばれる）が使用され、キーワード引数 `optimizer = LBFGS(;alphaguess = LineSearches.InitialStatic(;scaled=true))` で設定されます。ここで、ラインサーチアルゴリズムの初期ステップ長はキーワード引数 `alphaguess` を使用して選択されます（代替オプションについては [`LineSearches.jl`](https://github.com/JuliaNLSolvers/LineSearches.jl) パッケージを参照）。使用されるデフォルトのラインサーチアルゴリズムは `HagerZhang()` であり、代替手法はキーワード引数 `linesearch` を使用して指定できます（例: `linesearch = LineSearches.MoreThuente()`）。勾配ベースの他の手法も選択可能で、例えば、準ニュートン法 `BFGS` を `optimizer = Optim.BFGS()` で使用したり、小規模最適化問題には勾配フリー法のネルダー・ミード法を `optimizer = Optim.NelderMead()` で使用したりできます。関数 `J` とその勾配 `∇J` の計算には、安定システムのために [1] で開発された式が使用されます。各評価は、[2] で提案された方法を使用して周期的リャプノフ差分方程式のペアの解法を含みます。元のシステム `psys` が不安定な場合、安定化フィードバックの計算は、`A(t)/α` および制御行列 `B(t)/α` の形の修正された状態行列を持つシステムに対して同じ最適化技術を反復的に適用することによって行われます。ここで `α ≥ 1` は `A(t)/α` が安定であるように選択され、安定化が達成されるまで `α` の値は徐々に減少されます。安定化のための最適化手法はキーワード引数 `stabilizer` を使用して独立して選択でき、デフォルト設定は `stabilizer = LBFGS(;alphaguess = LineSearches.InitialStatic(;scaled=true))` です。安定化のみが望まれる場合は、`optimizer = nothing` を使用します。

内部最適化変数 `v` は、`m×p×ns` の配列として形成され、`v[:,:,i] := F_i` で、`i = 1, ..., ns` です。デフォルトでは、`v` は `v = 0`（すなわち、適切な次元のゼロ配列）として初期化されます。キーワード引数 `vinit = v0` を使用して、任意の `m×p×ns` 実配列 `v0` で `v` を初期化できます。

最適化プロセスは、いくつかのキーワードパラメータを使用して制御されます。キーワードパラメータ `maxiter = maxit` を使用して、実行される最大反復回数を指定できます（デフォルト: `maxit = 1000`）。キーワード引数 `vtol` は、最適化変数 `v` の変化における絶対許容誤差を指定するために使用できます（デフォルト: `vtol = 0`）。キーワード引数 `Jtol` は、最適化基準 `J` の変化における相対許容誤差を指定するために使用できます（デフォルト: `Jtol = 0`）、一方 `gtol` は勾配 `∇J` の絶対許容誤差を無限ノルムで指定するために使用できます（デフォルト: `gtol = 1e-5`）。キーワード引数 `show_trace = true` を使用すると、最適化アルゴリズムの状態のトレースが `stdout` に表示されます（デフォルト `show_trace = false`）。安定化の目的のために、値 `Jtol = 1.e-3`, `gtol = 1.e-2`, `maxit = 20` が使用され、より速い収束が促進されます。

返される名前付きタプル `info` には `(fopt, sdeg0, sdeg, vopt, optres)` が含まれます。ここで：

`info.fopt` は最適性能 `J` の結果値です；

`info.sdeg0` は閉ループ特性の固有値の初期安定度です；

`info.sdeg` は閉ループ特性の固有値の結果的な安定度です；

`info.vopt` は最適化変数 `v` の結果値です；

`info.optres` は [`Optim.jl`](https://github.com/JuliaNLSolvers/Optim.jl) パッケージの `Optim.optimize(...)` 関数によって返される結果です。このパッケージによって提供されるいくつかの関数を使用して、最適化結果に関連するさまざまな情報を照会できます（このパッケージのドキュメントを参照してください）。

境界制約付き最適化は、キーワード引数 `lub = (lb, ub)` を使用して実行できます。ここで `lb` は下限、`ub` はフィードバックゲインの上限です。デフォルトでは、`lub = missing` の場合、境界 `lb = -Inf` および `ub = Inf` が仮定されます。

*参考文献*

[1] A. Varga and S. Pieters. Gradient-based approach to solve optimal periodic output feedback problems.      Automatica, vol.34, pp. 477-481, 1998.

[2] A. Varga. Periodic Lyapunov equations: some applications and new algorithms.                Int. J. Control, vol, 67, pp, 69-87, 1997.
