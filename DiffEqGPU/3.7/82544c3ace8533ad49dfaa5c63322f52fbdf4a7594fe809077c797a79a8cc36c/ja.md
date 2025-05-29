```julia
EnsembleGPUKernel(backend, cpu_offload = 0.0)
```

全体のODEのためにユニークなGPUカーネルを生成する大規模並列アンサンブルアルゴリズムであり、その後実行されます。これにより、非常に低いオーバーヘッドのGPUコード生成が実現されますが、使用にいくつかの追加制限が課されます。

## 位置引数

  * `backend`: 計算を行うためのKernelAbstractionsバックエンド。
  * `cpu_offload`: CPUにオフロードする軌道の割合。デフォルトは0.0または0%の軌道です。

## 制限事項

  * すべての標準Julia `f`関数は許可されていません。GPUカーネルにコンパイル可能なJulia `f`関数のみが許可されています。これは特に、Juliaの特定の機能がカーネル内で問題を引き起こす可能性があることを意味します。例えば：

      * メモリの割り当て（配列の構築）
      * 線形代数（BLASを呼び出すもの）
      * ブロードキャスト
  * プレース外の`f`定義のみが許可されています。メモリ割り当てを許可しないという要件と組み合わさることで、ODEは`StaticArray`初期条件で定義されなければなりません。
  * 特定のODEソルバーのみが許可されています。これには以下が含まれます：

      * GPUTsit5
      * GPUVern7
      * GPUVern9
  * クラスター上で複数のGPUを使用するには、各GPUごとに手動で1つのプロセスを設定する必要があります。詳細については、マルチGPUチュートリアルを参照してください。

## 例

```julia
using DiffEqGPU, CUDA, OrdinaryDiffEq, StaticArrays

function lorenz(u, p, t)
    σ = p[1]
    ρ = p[2]
    β = p[3]
    du1 = σ * (u[2] - u[1])
    du2 = u[1] * (ρ - u[3]) - u[2]
    du3 = u[1] * u[2] - β * u[3]
    return SVector{3}(du1, du2, du3)
end

u0 = @SVector [1.0f0; 0.0f0; 0.0f0]
tspan = (0.0f0, 10.0f0)
p = @SVector [10.0f0, 28.0f0, 8 / 3.0f0]
prob = ODEProblem{false}(lorenz, u0, tspan, p)
prob_func = (prob, i, repeat) -> remake(prob, p = (@SVector rand(Float32, 3)) .* p)
monteprob = EnsembleProblem(prob, prob_func = prob_func, safetycopy = false)

@time sol = solve(
    monteprob, GPUTsit5(), EnsembleGPUKernel(CUDA.CUDABackend()), trajectories = 10_000,
    adaptive = false, dt = 0.1f0)
```
