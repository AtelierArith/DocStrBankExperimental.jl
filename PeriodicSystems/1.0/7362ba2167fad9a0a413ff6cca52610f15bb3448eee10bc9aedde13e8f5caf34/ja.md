```
pdpofstab_sw(psys, ns = missing; vinit, optimizer, maxit, vtol, Jtol, gtol, show_trace) -> (Fstab,info)
```

離散時間周期システム `psys = (A(t), B(t), C(t), D(t))` に対して、同じ周期の周期的出力フィードバックゲイン行列 `Fstab(t)` を決定します。この行列は、閉ループ状態行列 `A(t)+B(t)*Fstab(t)*inv(I-D(t)*Fstab(t))*C(t)` の特性指数 `Λ` が安定するようにします。システム `psys` の行列は `PeriodicArray` 型です。得られるスイッチング周期ゲイン `Fstab(t)` のスイッチング時間は、`N` 次元の整数ベクトル `ns` によって指定されます。デフォルトでは、`ns = [N]` であり、ここで `N` は最大サンプル数（すなわち、`N = psys.period/psys.Ts`）に対応し、定数ゲインに相当します。

出力フィードバックゲイン `Fstab(t)` は、`Fstab(t) = inv(I+F(t)D(t))*F(t)` として計算され、`F(t)` は次のように定義されます。

```
F(t) = F_i for t ∈ [ns[i]Δ,ns[i+1]Δ) and i ∈ {1, ..., N-1}, or
F(t) = F_N for t ∈ [ns[N]Δ,T),
```

ここで `T` はシステムの周期（すなわち、`T = psys.period`）、`Δ` はシステムのサンプリング時間（すなわち、`Δ = psys.Ts`）、`F_i` は `i` 番目のゲインです。得られる周期行列 `Fstab(t)` は `SwitchingPeriodicArray` 型です。対応する閉ループ周期システムは、関数 [`psfeedback`](@ref) を使用して取得できます。

最適フィードバックゲイン `F_i` を `i = 1, ...., N` のために決定するために、最適化パッケージ [`Optim.jl`](https://github.com/JuliaNLSolvers/Optim.jl) にあるツールを使用した最適化ベースのアプローチが採用されます。デフォルトでは、制約のない最小化のために勾配フリーの *Nelder-Mead* ローカルサーチ法が使用され、キーワード引数 `optimizer = Optim.NelderMead()` が設定されます。代替の勾配フリーの *Simulated Annealing* グローバルサーチ法は、`optimizer = Optim.SimulatedAnnealing()` で選択できます。

`m` 入力と `p` 出力を持つシステムの場合、内部最適化変数 `v` が使用され、`m×p×N` 配列として定義されます。デフォルトでは、`v` は `v = 0`（すなわち、適切な次元のゼロ配列）として初期化されます。キーワード引数 `vinit = v0` を使用して、任意の `m×p×N` 配列 `v0` で `v` を初期化できます。

最小化すべき性能指標は `J := sdeg(v)` であり、ここで `sdeg(v)` は特性指数の最大モジュラスとして定義される安定度です。最適化プロセスは、いくつかのキーワードパラメータを使用して制御されます。キーワードパラメータ `maxit` を使用して、実行される最大反復回数を指定できます（デフォルト: `maxit = 1000`）。キーワード引数 `vtol` を使用して、最適化変数 `v` の変化における絶対許容誤差を指定できます（デフォルト: `vtol = 0`）。キーワード引数 `Jtol` を使用して、最適化基準 `J` の変化における相対許容誤差を指定できます（デフォルト: `Jtol = 0`）、一方 `gtol` はメソッド特有の主収束許容誤差です（デフォルト: `gtol = 1e-3`）。キーワード引数 `show_trace = true` を使用すると、最適化アルゴリズムの状態のトレースが `stdout` に表示されます（デフォルト `show_trace = false`）。 （追加情報については、[Optim.jl](https://github.com/JuliaNLSolvers/Optim.jl) パッケージのドキュメントを参照してください）。

返される名前付きタプル `info` には `(fopt, sdeg0, sdeg, vopt, optres)` が含まれ、次のようになります。

`info.fopt` は最適な性能 `J` の結果値です。

`info.sdeg0` は閉ループ特性指数の初期安定度です。

`info.sdeg` は閉ループ特性指数の結果的な安定度です。

`info.vopt` は最適化変数 `v` の結果値です。

`info.optres` は [`Optim.jl`](https://github.com/JuliaNLSolvers/Optim.jl) パッケージの `Optim.optimize(...)` 関数によって返される結果です。このパッケージによって提供されるいくつかの関数を使用して、最適化結果に関連するさまざまな情報を照会できます（このパッケージのドキュメントを参照してください）。
