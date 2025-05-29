```
CoupledSDEs <: ContinuousTimeDynamicalSystem
CoupledSDEs(f, u0 [, p]; kwargs...)
```

確率的連続時間動的システムは、以下の一連の結合された確率微分方程式（SDE）によって定義されます：

$$
\text{d}\mathbf{u} = \mathbf{f}(\mathbf{u}, p, t) \text{d}t + \mathbf{g}(\mathbf{u}, p, t) \text{d}\mathcal{N}_t
$$

ここで、$\mathbf{u}(t)$は時刻$t$における状態ベクトル、$\mathbf{f}$は決定論的ダイナミクスを記述し、ノイズ項$\mathbf{g}(\mathbf{u}, p, t) \text{d}\mathcal{N}_t$はノイズ関数（または*拡散関数*）$\mathbf{g}$とノイズプロセス$\mathcal{N}_t$の観点から確率的強制を記述します。関数$\mathcal{f}$と$\mathcal{g}$のパラメータはベクトル$p$に含まれています。

確率的強制のタイプに応じて、`CoupledSDEs`を構築する方法はいくつかあります。

必要な位置引数は、決定論的動的ルール`f(u, p, t)`、初期状態`u0`、およびオプションでパラメータコンテナ`p`（デフォルトは`p = nothing`）です。`f, u0`に関する構築手順については、[DynamicalSystems.jl チュートリアル](https://juliadynamics.github.io/DynamicalSystemsDocs.jl/dynamicalsystems/dev/tutorial/)を参照してください。

デフォルトでは、ノイズ項は標準ブラウン運動、すなわち単純なガウスホワイトノイズで、単位共分散行列を持ちます。異なるノイズ構造を構築するには、以下を参照してください。

## ノイズ項

ノイズ項は、いくつかのキーワード引数を介して指定できます。これらのキーワード引数に基づいて、ノイズ関数`g`は明示的に与えられない限り、内部で構築されます。

  * ノイズ強度（すなわち、確率的強制の大きさ）は、`noise_strength`でスケーリングできます（デフォルトは`1.0`）。この係数は、全体のノイズ項に掛けられます。
  * 非対角および相関のあるノイズの場合、共分散行列を`covariance`で提供できます（デフォルトは`length(u0)`の単位行列）。
  * 状態依存および時間依存のノイズを含む、より複雑なノイズ構造の場合、ノイズ関数`g`をキーワード引数として明示的に提供できます（デフォルトは`nothing`）。構築手順については、読み続けてください。

関数`g`は、DynamicalSystems.jlの[`SDEProblem`](https://docs.sciml.ai/DiffEqDocs/stable/types/sde_types/#SciMLBase.SDEProblem)で指定された拡散関数にインターフェースします。`g`は、`f`と同じ構文に従う必要があります。すなわち、`g(u, p, t)`はアウトオブプレイス（oop）用、`g!(du, u, p, t)`はインプレース（iip）用です。

`g`がベクトル形式であり、対角ノイズを記述する場合を除き、`g`の出力のプロトタイプ型インスタンスはキーワード引数`noise_prototype`を介して指定する必要があります。これは、[`LinearAlgebra.mul!(Y, A, B) -> Y`](https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/#LinearAlgebra.mul!)メソッドが定義されている任意の型`A`であることができます。一般的には、これは行列またはスパース行列です。これが指定されない場合、デフォルトは`nothing`となり、`g`は対角であると解釈されます。

ノイズプロセスは`noise_process`を介して指定できます。デフォルトは標準ウィーナープロセス（ガウスホワイトノイズ）です。ノイズプロセスの定義に関する詳細は、[DiffEqNoiseProcess.jl](https://docs.sciml.ai/DiffEqNoiseProcess/stable/)のドキュメントを参照してください。事前定義されたプロセスの完全なリストは[こちら](https://docs.sciml.ai/DiffEqNoiseProcess/stable/noise_processes/)で見つけることができます。`DiffEqNoiseProcess.jl`には、カスタムノイズプロセスを定義するためのインターフェースもあります。

`g`と`noise_process`を組み合わせることで、さまざまなタイプの確率的システムを定義できます。さまざまなタイプの確率的システムの例は、[StochasticDiffEq.jl チュートリアルページ](https://docs.sciml.ai/DiffEqDocs/stable/tutorials/sde_example/)にリストされています。一般的なタイプの確率的システムの簡単な概要は、[`CoupledSDEs`のオンラインドキュメント](https://docs.sciml.ai/DiffEqDocs/stable/tutorials/sde_example/)でも見つけることができます。

## キーワード引数

  * `g`: ノイズ関数（デフォルト`nothing`）
  * `noise_strength`: ノイズ強度のスケーリング係数（デフォルト`1.0`）
  * `covariance`: ノイズ共分散行列（デフォルト`nothing`）
  * `noise_prototype`: `g`の出力のプロトタイプインスタンス（デフォルト`nothing`）
  * `noise_process`: [DiffEqNoiseProcess.jl](https://docs.sciml.ai/DiffEqNoiseProcess/stable/)によって提供される確率プロセス（デフォルト`nothing`、すなわち標準ウィーナープロセス）
  * `t0`: 初期時間（デフォルト`0.0`）
  * `diffeq`: DiffEqソルバー設定（以下を参照）
  * `seed`: ランダム数シード（デフォルト`UInt64(0)`）

## DifferentialEquations.jlとのインターフェース

`CoupledSDEs`は、DifferentialEquations.jlのソルバーを使用して進化します。`diffeq`キーワード引数を介してソルバーを指定するには、フラグ`alg`を使用します。これは、StochasticDiffEq.jlをロードした後にアクセスできます（`using StochasticDiffEq`）。デフォルトの`diffeq`は次のとおりです：

```julia
(alg = SOSRA(), abstol = 1.0e-2, reltol = 1.0e-2)
```

`diffeq`のキーワードには、[イベント処理](https://docs.sciml.ai/DiffEqDocs/stable/features/callback_functions/)のための`callback`も含めることができます。

開発ノート：`CoupledSDEs`は、StochasticDiffEq.jlの`SDEIntegrator`の軽量ラッパーです。インテグレーターはフィールド`integ`として利用可能で、`SDEProblem`は`integ.sol.prob`です。問題を抽出するための便利な構文`SDEProblem(ds::CoupledSDEs, tspan = (t0, Inf))`が利用可能です。

## `CoupledSDEs`と`CoupledODEs`の間の変換

`CoupledSDEs`システムを`CoupledODEs`に変換して、その決定論的部分を分析するには、関数`CoupledODEs(ds::CoupledSDEs; diffeq, t0)`を使用します。同様に、`CoupledODEs`を`CoupledSDEs`に変換するには、`CoupledSDEs(ds::CoupledODEs, p; kwargs...)`を使用します。 ```
