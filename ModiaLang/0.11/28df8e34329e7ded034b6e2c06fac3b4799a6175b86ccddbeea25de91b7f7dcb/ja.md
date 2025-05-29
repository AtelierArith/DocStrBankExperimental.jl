```
solution = simulate!(instantiatedModel [, algorithm];
          merge            = missing,  # パラメータ/初期/開始値を変更
          tolerance        = 1e-6,     # 相対許容誤差
          startTime        = 0.0,
          stopTime         = 0.0,      # stopTime >= startTime が必要
          interval         = missing,  # = (stopTime-startTime)/500
          interp_points    = 0,
          dtmax            = missing,  # = 100*interval
          adaptive         = true,
          nlinearMinForDAE = 10,
          log              = false,
          logStates        = false,
          logEvents        = false,
          logProgress      = false,
          logTiming        = false,
          logParameters    = false,
          logEvaluatedParameters   = false,
          requiredFinalStates      = missing
          requiredFinalStates_rtol = 1e-3,
          requiredFinalStates_atol = 0.0,
          useRecursiveFactorizationUptoSize = 0)
```

`instantiatedModel::SimulationModel` を `algorithm` (= [DifferentialEquations.jl](https://diffeq.sciml.ai/stable/solvers/ode_solve/) の ODE Solvers または [DAE Solvers](https://diffeq.sciml.ai/stable/solvers/dae_solve/)) でシミュレーションします。

`algorithm` 引数が欠けている場合、`algorithm=Sundials.CVODE_BDF()` が使用されます。ただし、instantiatedModel の `FloatType = Float64` が必要です。それ以外の場合、DifferentialEquations からデフォルトのアルゴリズムが選択されます（詳細は [https://arxiv.org/pdf/1807.06430](https://arxiv.org/pdf/1807.06430)、図3を参照）。`CVODE_BDF` と `IDA` のシンボルは ModiaLang からエクスポートされているため、`simulate!(instantiatedModel, CVODE_BDF(), ...)` および `simulate!(instantiatedModel, IDA(), ...)` を使用できます（`import Sundials; simulate!(instantiatedModel, Sundials.xxx(), ...)` の代わりに）。

シミュレーション結果は `instantiatedModel` に保存され、`plot(instantiatedModel, ...)` でプロットでき、`rawSignal(..)` または `getPlotSignal(..)` で結果値を取得できます。`printResultInfo(instantiatedModel)` は結果ファイル内の信号に関する情報を印刷します。詳細については、章 [Results and Plotting](@ref) を参照してください。

（オプションの）戻り値 `solution` は `DifferentialEquations.solve(..)` からの戻り値であり、したがって `DifferentialEquations.jl` のすべての後処理機能を使用できます。特に、

  * solution.t[i] # ストレージポイント i での時間瞬間（solution.t[end] = stopTime）
  * solution.u[i] # ストレージポイント i での状態

シミュレーションの実行は `<CTRL> C` (SIGINT) で中止できます。

# オプション引数

  * `merge`: シミュレーションが開始される前に、`model` に保存されている以前の値とマージされるパラメータおよび初期/開始値を定義します。たとえば、モデル内で初期値 `phi = Var(init=1.0)` が定義されている場合、`merge = Map(phi=2.0)` で異なる初期値を提供できます。
  * `tolerance`: 相対許容誤差。
  * `startTime`: 開始時間。値に単位がない場合、単位 [s] があると見なされます。
  * `stopTime`: 停止時間。値に単位がない場合、単位 [s] があると見なされます。
  * `interval`: 結果を保存する間隔。`interval=missing` の場合、内部的に (stopTime-startTime)/500 として選択されます。値に単位がない場合、単位 [s] があると見なされます。
  * `interp_points`: 定義された交差関数がある場合、1ステップあたりの追加の補間ポイントの数。
  * `dtmax`: 最大ステップサイズ。`dtmax==missing` の場合、内部的に `100*interval` に設定されます。
  * `adaptive`: `algorithm` がステップサイズ制御を使用する場合は true (利用可能な場合)。`algorithm` が固定ステップサイズ `interval` を使用する場合は false (利用可能な場合)。
  * `nlinearMinForDAE`: `algorithm` が DAE インテグレータ（例：`IDA()`）であり、線形方程式系のサイズが `>= nlinearMinForDAE` であり、この方程式系の反復変数が DAE 状態導関数のサブセットである場合、連続統合中（ただしイベントや初期化時を除く）にこの方程式系はローカルに解かれず、DAE インテグレータを介して解かれます。通常、大きな線形方程式系の場合、そのような場合にシミュレーション効率が大幅に向上します。
  * `log`: = true の場合、シミュレーションをログします。
  * `logStates`: = true の場合、状態、その初期/開始値、およびその単位をログします。
  * `logEvents`: = true の場合、イベントをログします。
  * `logProgress` = true の場合、5秒ごとに現在のシミュレーション時間を出力します。
  * `logTiming`: = true の場合、`instantiatedModel.timer` でタイミングをログします。これは [TimerOutputs](https://github.com/KristofferC/TimerOutputs.jl).TimerOutput のインスタンスです。ユーザー関数は、次のようにタイミングを含めることができます。              `TimerOutputs.@timeit instantiatedModel.timer "My Timing" <statement>`。
  * `logParameters`: = true の場合、モデルで定義されたパラメータおよび初期/開始値をログします。
  * `logEvaluatedParameters`: = true の場合、初期化およびシミュレーション中に使用される評価されたパラメータおよび初期/開始値をログします。
  * `requiredFinalStates`: `missing` でない場合：最終時間瞬間での ODE 状態ベクトルが、相対許容誤差 `requiredFinalStates_rtol` に関してベクトル `requiredFinalStates` と一致するかどうかを `@test` でテストします。これが満たされない場合、最終状態ベクトルを印刷します（これにより、simulate!(..) 呼び出しにコピー＆ペーストできます）。
  * `requiredFinalStates_rtol`: `requiredFinalStates` に使用される相対許容誤差。
  * `requiredFinalStates_atol`: `requiredFinalStates` に使用される絶対許容誤差（`?isapprox` の atol を参照）。
  * `useRecursiveFactorizationUptoSize`: = 0: 線形方程式系 A*v=b は、`length(v) <= useRecursiveFactorizationUptoSize` の場合、デフォルトの `lu!(..)` および `ldiv!(..)` の代わりに `RecursiveFactorization.jl` で解かれます。`RecursiveFactorization.jl` の文書によると、`length(v) <= 500` の場合、OpenBLAS を使用した `lu!(..)` よりも速いです（通常、2倍以上のファクター）。`lu!(..)!` が成功したが、`RecursiveFactorization.jl` が特異系のために失敗したケースがあったため、デフォルトは `lu!(..)!` を使用します。

# 例

```julia
using Modia
@usingModiaPlot

# モデルを定義
inputSignal(t) = sin(t)

FirstOrder = Model(
    T = 0.2,
    x = Var(init=0.3),
    equations = :[u = inputSignal(time/u"s"),
                  T * der(x) + x = u,
                  y = 2*x]
)

# モデルのパラメータと初期値を変更
FirstOrder2 = FirstOrder | Map(T = 0.4, x = Var(init=0.6))

# モデルをインスタンス化
firstOrder = @instantiateModel(FirstOrder2, logCode=true)


# 自動的に選択されたアルゴリズム (Sundials.CVODE_BDF()) でシミュレーション
# 変更されたパラメータと初期値を使用
simulate!(firstOrder, stopTime = 1.0, merge = Map(T = 0.6, x = 0.9), logEvaluatedParameters=true)

# 図1に変数 "x", "u" をプロットし、図2に "der(x)" をプロットし、両方の図を図3に表示
plot(firstOrder, [("x","u"), "der(x)"], figure=3)

# "time" と "u" の値を取得：
usig = getPlotSignal(firstOrder, "x")
       # usig.xsig      : 時間ベクトル
       # usig.xsigLegend: 時間ベクトルの凡例
       # usig.ysig      : "x" ベクトル
       # usig.ysigLegend: "x" ベクトルの凡例
       # usig.ysigType  : ModiaResult.Continuous または ModiaResult.Clocked

# ステップサイズ制御を使用して Runge-Kutta 5/4 でシミュレーション
simulate!(firstOrder, Tsit5(), stopTime = 1.0)

# 固定ステップサイズで Runge-Kutta 4 でシミュレーション
simulate!(firstOrder, RK4(), stopTime = 1.0, adaptive=false)

# 非剛性領域では Verners Runge-Kutta 6/5 アルゴリズムに切り替え、
# 剛性領域では Rosenbrock 4 (= A安定法) でステップサイズ制御を使用してシミュレーション
simulate!(firstOrder, AutoVern6(Rodas4()), stopTime = 1.0)
```
