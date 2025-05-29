```julia
struct Flow{TF, Tf, Tts, Tff, Td, Tad, Tse, Tprob, TprobMono, Tfs, Tcb, Tδ} <: BifurcationKit.AbstractFlow
```

  * `F::Any`: Cauchy問題に関連付けられたベクトル場 `(x, p) -> F(x, p)`。シューティング問題の微分に使用されます。デフォルト: nothing
  * `flow::Any`: Cauchy問題に関連付けられた流れ（または半群）`(x, p, t) -> flow(x, p, t)`。最後の時間点のみが (u = ...) の形式で返される必要があります。デフォルト: nothing
  * `flowTimeSol::Any`: タプル (t, u(t)) を返す流れ。オプションで、主にユーザー側でのプロットに使用されます。デフォルト: nothing
  * `flowFull::Any`: [オプション] Cauchy問題に関連付けられた流れ（または半群）`(x, p, t) -> flow(x, p, t)`。時間区間 [0,t] の全解が返される必要があります。これを提供することは厳密には必要ありませんが、主にユーザー側でのプロットに使用されます。デフォルトとして `nothing` を使用してください。デフォルト: nothing
  * `jvp::Any`: 流れの微分 `dflow` *w.r.t.* `x`、`(x, p, dx, t) -> dflow(x, p, dx, t)`。重要な点は、`dflow(x, dx, t)` が Named Tuple を返すことを要求することです: `(t = t, u = flow(x, p, t), du = dflow(x, p, dx, t))`、最後のコンポーネントは流れの導関数の値です。デフォルト: nothing
  * `vjp::Any`: 流れの随伴微分 `vjpflow` *w.r.t.* `x`、`(x, p, dx, t) -> vjpflow(x, p, dx, t)`。重要な点は、`vjpflow(x, p, dx, t)` が Named Tuple を返すことを要求することです: `(t = t, u = flow(x, p, t), du = vjpflow(x, p, dx, t))`、最後のコンポーネントは流れの導関数の値です。デフォルト: nothing
  * `jvpSerial::Any`: [オプション] dflow の直列バージョン。並列の複数シューティングを使用する際に内部で使用されます。デフォルトとして `nothing` を使用してください。デフォルト: nothing
  * `prob::Any`: [内部] Cauchy問題の流れに関連付けられた ODEProblem を格納します。デフォルト: nothing
  * `probMono::Any`: [内部] 変分問題の流れに関連付けられた ODEProblem を格納します。デフォルト: nothing
  * `flowSerial::Any`: [内部] 流れの直列バージョン。デフォルト: nothing
  * `callback::Any`: [内部] 可能なコールバックを格納します。デフォルト: nothing
  * `delta::Any`: [内部] デフォルト: 1.0e-8

# 簡略化されたコンストラクタ

ベクトル場 `F`、流れ `ϕ` およびその微分 `dϕ` のみを渡す簡単なコンストラクタを提供します:

```
fl = Flow(F, ϕ, dϕ)
```

# DifferentialEquations.jl 用の簡略化されたコンストラクタ

これらは、`DifferentialEquations.jl` からの `prob::ODEProblem` または `prob::EnsembleProblem`（並列計算用）と、`Tsit5()` のような ODE 時間ステッパーを渡すだけの簡単なコンストラクタです。したがって、例えば次のようにできます。

```
fl = Flow(prob, Tsit5(); kwargs...)
```

ここで `kwargs` は `SciMLBase::solve` に渡されます。ベクトル場がパラメータ `p` に依存する場合、次のように `Flow` を定義できます。

```
fl = Flow(prob, Tsit5(); kwargs...)
```

最後に、2つの `ODEProblem` を渡すことができ、2つ目は変分方程式を計算するために使用されます。

```
fl = Flow(prob1::ODEProblem, alg1, prob2::ODEProblem, alg2; kwargs...)
```
