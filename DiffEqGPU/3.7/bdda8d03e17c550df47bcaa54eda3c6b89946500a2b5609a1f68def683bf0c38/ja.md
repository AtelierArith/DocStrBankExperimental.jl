```julia
EnsembleGPUArray(backend, cpu_offload = 0.2)
```

各ODE解をそれぞれのカーネル上の別々のODE積分器で並列化するためにGPUカーネルを利用する`EnsembleArrayAlgorithm`。

## 位置引数

  * `backend`: 計算を行うためのKernelAbstractionsバックエンド。
  * `cpu_offload`: CPUにオフロードする軌道の割合。デフォルトは0.2、すなわち20%の軌道。

## 制限事項

`EnsembleGPUArray`は、KernelAbstractons.jlを使用して`f`のカーネルを生成し、`CuArray`入力タイプで定義された結果のODEを解くことができる必要があります。これにより、使用に関する以下の制限が導入されます：

  * すべての標準Julia `f`関数は許可されているわけではありません。GPUカーネルにコンパイル可能なJulia `f`関数のみが許可されます。これは特に、Juliaの特定の機能がカーネル内で問題を引き起こす可能性があることを意味します。例えば：

      * メモリの割り当て（配列の構築）
      * 線形代数（BLASを呼び出すもの）
      * ブロードキャスト
  * すべてのODEソルバーは許可されているわけではなく、OrdinaryDiffEq.jlのもののみが許可されています。OrdinaryDiffEq.jlからのテストされた機能セットには以下が含まれます：

      * 明示的ルンゲクッタ法
      * 暗黙的ルンゲクッタ法
      * ローゼンブロック法
      * DiscreteCallbacksおよびContinuousCallbacks
  * 硬いODEは、必要なすべての導関数関数の解析解を必要とします。例えば、ローゼンブロック法はヤコビアンと時間に関する勾配を必要とし、これらの2つの関数を提供する必要があります。これらは[modelingtoolkitize](https://docs.juliadiffeq.org/latest/tutorials/advanced_ode_example/#Automatic-Derivation-of-Jacobian-Functions-1)アプローチによって生成できます。
  * クラスター上で複数のGPUを使用するには、各GPUごとに手動で1つのプロセスを設定する必要があります。詳細については、マルチGPUチュートリアルを参照してください。

!!! warn
    `terminate!`を使用したコールバックは、任意の軌道が停止すると全体の積分が停止するため、`EnsembleGPUArray`ではうまく機能しません。使用には注意が必要です。


## 例

```julia
using DiffEqGPU, CUDA, OrdinaryDiffEq
function lorenz(du, u, p, t)
    du[1] = p[1] * (u[2] - u[1])
    du[2] = u[1] * (p[2] - u[3]) - u[2]
    du[3] = u[1] * u[2] - p[3] * u[3]
end

u0 = Float32[1.0; 0.0; 0.0]
tspan = (0.0f0, 100.0f0)
p = [10.0f0, 28.0f0, 8 / 3.0f0]
prob = ODEProblem(lorenz, u0, tspan, p)
prob_func = (prob, i, repeat) -> remake(prob, p = rand(Float32, 3) .* p)
monteprob = EnsembleProblem(prob, prob_func = prob_func, safetycopy = false)
@time sol = solve(monteprob, Tsit5(), EnsembleGPUArray(CUDADevice()),
    trajectories = 10_000, saveat = 1.0f0)
```
