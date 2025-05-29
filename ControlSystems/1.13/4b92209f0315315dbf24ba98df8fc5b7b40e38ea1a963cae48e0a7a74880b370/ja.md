```
res = lsim(sys::DelayLtiSystem, u, t::AbstractArray{<:Real}; x0=fill(0.0, nstates(sys)), alg=MethodOfSteps(Tsit5()), abstol=1e-6, reltol=1e-6, force_dtmin=true, kwargs...)
```

システム `sys` を時間 `t` にわたって、入力信号 `u` を使用して、初期状態 `x0` で、メソッド `alg` を使用してシミュレートします。

引数:

`t`: 等間隔の時間サンプルを持つ `AbstractVector` でなければなりません（`t[i] - t[i-1]` が一定） `u`: 時間 `t` における制御信号 `uₜ` を決定するための関数で、以下のいずれかの形式を取ります：

  * `u`: 時間 `t` における制御信号 `uₜ` を決定するための関数で、以下のいずれかの形式を取ります：

      * 定数 `Number` または `Vector`、定常入力として解釈されます。
      * 内部状態と時間を受け取る関数 `u(x, t)`。注意、遅延システムの状態表現は有理システムのそれとは異なります。
      * インプレース関数 `u(uₜ, x, t)`。（わずかに効率的）

`alg, abstol, reltol` および `kwargs...`: は `DelayDiffEq.solve` に送信されます。

このメソッドは、デフォルトで `force_dtmin=true` を設定して、例えばステップ入力によって示される不連続性を処理します。これにより、ソルバーが早期に警告を出すのではなく、悪条件の問題を解決するのに長い時間がかかる可能性があります。

[`SimResult`](@ref) のインスタンスを返し、これは直接プロットするか、`y, t, x, u = res` に分解することができます。
