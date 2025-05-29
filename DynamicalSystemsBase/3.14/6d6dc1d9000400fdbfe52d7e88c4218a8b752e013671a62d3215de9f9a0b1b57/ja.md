```
CoupledODEs <: ContinuousTimeDynamicalSystem
CoupledODEs(f, u0 [, p]; diffeq, t0 = 0.0)
```

以下のように、連立常微分方程式のセットによって定義される決定論的連続時間動的システム：

$$
\frac{d\vec{u}}{dt} = \vec{f}(\vec{u}, p, t)
$$

`CoupledODE`の別名は`ContinuousDynamicalSystem`です。

オプションで、パラメータコンテナ`p`と初期時間をキーワード`t0`として提供できます。

`f, u0`に関する構築手順については、DynamicalSystems.jlのチュートリアルを参照してください。

## DifferentialEquations.jlとのインターフェース

ODEはDifferentialEquations.jlのソルバーによって進化します。`CoupledODEs`を初期化する際に、`f`を時間的に統合するソルバーを指定し、他の統合オプションを`diffeq`キーワードを使用して指定できます。例えば、`diffeq = (abstol = 1e-9, reltol = 1e-9)`のように使用できます。ソルバーを指定したい場合は、キーワード`alg`を使用して指定します。例：`diffeq = (alg = Tsit5(), reltol = 1e-6)`。これには、最初に`using OrdinaryDiffEq`（または`OrdinaryDiffEqVerner`のような小さなライブラリパッケージ）を使用してソルバーにアクセスする必要があります。デフォルトの`diffeq`は次の通りです：

(alg = OrdinaryDiffEqTsit5.Tsit5{typeof(OrdinaryDiffEqCore.trivial*limiter!), typeof(OrdinaryDiffEqCore.trivial*limiter!), Static.False}(OrdinaryDiffEqCore.trivial*limiter!, OrdinaryDiffEqCore.trivial*limiter!, static(false)), abstol = 1.0e-6, reltol = 1.0e-6)

`diffeq`キーワードには、[イベント処理](http://docs.juliadiffeq.org/latest/features/callback_functions.html)のための`callback`も含めることができます。

便利なコンストラクタ`CoupledODEs(prob::ODEProblem [, diffeq])`および`CoupledODEs(ds::CoupledODEs [, diffeq])`も利用可能です。問題を取得するには、`ODEProblem(ds::CoupledODEs, tspan = (t0, Inf))`を使用します。

ModelingToolkit.jlと統合するには、動的システムは**必ず**`ODEProblem`を介して作成される必要があります（これはModelingToolkit.jlを介して作成されます）。例についてはチュートリアルを参照してください。

開発メモ：`CoupledODEs`はDifferentialEquations.jlの`ODEIntegrator`の軽量ラッパーです。 ```
