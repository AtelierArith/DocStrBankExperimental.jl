```
pcpofstab_sw(psys, ts = missing; K = 100, vinit, optimizer, maxit, vtol, Jtol, gtol, show_trace) -> (Fstab,info)
```

周期 `T` の連続時間周期システム `psys = (A(t), B(t), C(t), D(t))` に対して、同じ周期と切替時間 `ts` の周期的出力フィードバックゲイン行列 `Fstab(t)` を決定します。これにより、閉ループ状態行列 `A(t)+B(t)*Fstab(t)*inv(I-D(t)*Fstab(t))*C(t)` の特性指数 `Λ` が安定します。システム `psys` の行列は `PeriodicFunctionMatrix` 型です。ベクトル `ts` に含まれる `ns` の切替時間は `0 = ts[1] < ts[2] < ... < ts[ns] < T` を満たさなければなりません。もし `ts = missing` の場合、デフォルトで `ts = [0]` が使用されます（すなわち、定常出力フィードバック）。

出力フィードバックゲイン `Fstab(t)` は `Fstab(t) = inv(I+F(t)D(t))*F(t)` として計算され、`F(t)` は次のように定義されます。

```
 F(t) = F_i  for t ∈ [ts[i],ts[i+1]) and i ∈ {1, ..., ns-1} or 
 F(t) = F_ns for t ∈ [ts[ns],T)
```

ここで `F_i` は `i` 番目のゲインです。結果として得られる周期行列 `Fstab(t)` は `PeriodicSwitchingMatrix` 型です。対応する閉ループ周期システムは関数 [`psfeedback`](@ref) を使用して取得できます。

最適フィードバックゲイン `F_i` を `i = 1, ...., ns` のために決定するために、最適化パッケージ [`Optim.jl`](https://github.com/JuliaNLSolvers/Optim.jl) にあるツールを使用した最適化ベースのアプローチが採用されます。デフォルトでは、制約のない最小化のために勾配フリーの *Nelder-Mead* ローカルサーチ法が使用され、キーワード引数 `optimizer = Optim.NelderMead()` が設定されます。代替の勾配フリーの *Simulated Annealing* グローバルサーチ法は `optimizer = Optim.SimulatedAnnealing()` で選択できます。

`m` 入力と `p` 出力を持つシステムの場合、内部最適化変数 `v` が使用され、`v[:,:,i] := F_i` という形で `m×p×ns` 配列として形成されます（`i = 1, ..., ns` の場合）。最小化すべき性能指標は `J := sdeg(v)` であり、ここで `sdeg(v)` は `Af(t) := A(t)+B(t)*F(t)*C(t)` の特性指数の最大実部として定義される安定度です。キーワード引数 `K` は、特性指数を評価する際に `Af(t)` のモノドロミー行列を表現するために使用される因子の数です（デフォルト: `K = 100`）。デフォルトでは、`v` は `v = 0`（すなわち、適切な次元のゼロ配列）として初期化されます。キーワード引数 `vinit = v0` を使用して、任意の `m×p×ns` 配列 `v0` で `v` を初期化できます。

最適化プロセスは、いくつかのキーワードパラメータを使用して制御されます。キーワードパラメータ `maxit` を使用して、実行される最大反復回数を指定できます（デフォルト: `maxit = 1000`）。キーワード引数 `vtol` を使用して、最適化変数 `v` の変化における絶対許容誤差を指定できます（デフォルト: `vtol = 0`）。キーワード引数 `Jtol` を使用して、最適化基準 `J` の変化における相対許容誤差を指定できます（デフォルト: `Jtol = 0`）、一方 `gtol` はメソッド特有の主収束許容誤差です（デフォルト: `gtol = 1e-3`）。キーワード引数 `show_trace = true` を使用すると、最適化アルゴリズムの状態のトレースが `stdout` に表示されます（デフォルト `show_trace = false`）。 （追加情報については、[Optim.jl](https://github.com/JuliaNLSolvers/Optim.jl) パッケージのドキュメントを参照してください）。

返される名前付きタプル `info` には `(fopt, sdeg0, sdeg, vopt, optres)` が含まれます。ここで：

`info.fopt` は最適な性能 `J` の結果値です。

`info.sdeg0` は閉ループ特性指数の初期安定度です。

`info.sdeg` は閉ループ特性指数の結果としての安定度です。

`info.vopt` は最適化変数 `v` の結果値です。

`info.optres` は [`Optim.jl`](https://github.com/JuliaNLSolvers/Optim.jl) パッケージの `Optim.optimize(...)` 関数によって返される結果です。このパッケージによって提供されるいくつかの関数を使用して、最適化結果に関連するさまざまな情報を照会できます（このパッケージのドキュメントを参照してください）。
