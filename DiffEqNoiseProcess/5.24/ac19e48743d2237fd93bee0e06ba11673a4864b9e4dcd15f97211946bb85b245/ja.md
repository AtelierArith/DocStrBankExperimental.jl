```julia
NoiseWrapper{T, N, Tt, T2, T3, T4, ZType, inplace} <:
AbstractNoiseProcess{T, N, Vector{T2}, inplace}
```

これは古いノイズプロセスから新しいノイズプロセスを生成し、その補間を使用してノイズを生成します。これにより、同じタイムステップだけでなく、新しい（適応的な）タイムステップでも以前のノイズプロセスを再利用することができます。したがって、これはマルチレベルモンテカルロスキームや強収束テストを行うのに非常に良いです。

## コンストラクタ

```julia
NoiseWrapper(source::AbstractNoiseProcess{T, N, Vector{T2}, inplace};
    reset = true, reverse = false, indx = nothing) where {T, N, T2, inplace}
```

## NoiseWrapperの例

この例では、SDEを3回解きます：

  * 最初に、ノイズプロセスを生成するため
  * 2回目に、同じタイムステップで値が同じであることを示すため
  * 3回目に、半分のサイズのタイムステップで

最初に、SDEを解くことでノイズプロセスを生成します：

```julia
using StochasticDiffEq, DiffEqNoiseProcess
f1(u, p, t) = 1.01u
g1(u, p, t) = 1.01u
dt = 1 // 2^(4)
prob1 = SDEProblem(f1, g1, 1.0, (0.0, 1.0))
sol1 = solve(prob1, EM(), dt = dt, save_noise = true)
```

次に、ノイズをNoiseWrapperにラップし、同じ問題を解きます：

```julia
W2 = NoiseWrapper(sol1.W)
prob1 = SDEProblem(f1, g1, 1.0, (0.0, 1.0), noise = W2)
sol2 = solve(prob1, EM(), dt = dt)
```

次のテストを行うことができます：

```julia
@test sol1.u ≈ sol2.u
```

値が本質的に等しいことを確認します。次に、同じプロセスを使用して、より小さな`dt`で同じ軌道を解くことができます：

```julia
W3 = NoiseWrapper(sol1.W)
prob2 = SDEProblem(f1, g1, 1.0, (0.0, 1.0), noise = W3)

dt = 1 // 2^(5)
sol3 = solve(prob2, EM(), dt = dt)
```

結果をプロットして、どのように見えるかを確認します：

```julia
using Plots
plot(sol1)
plot!(sol2)
plot!(sol3)
```

![noise_process](assets/noise_process.png)

このプロットでは、`sol2`が`sol1`を覆っています。なぜなら、ほぼ同じ値に達しているからです。`sol3`は他のものと似ていることがわかります。なぜなら、同じ基盤のノイズプロセスを使用しているからです。ただし、はるかに細かくサンプリングされています。

再確認のために、次のことを確認します：

```julia
plot(sol1.W)
plot!(sol2.W)
plot!(sol3.W)
```

![coupled_wiener](assets/coupled_wiener.png)

結合されたウィーナープロセスは、すべての他の時間点で一致し、中間の時間点はブラウン橋に従って計算されました。

### 適応型NoiseWrapperの例

ここでは、同じノイズを`NoiseWrapper`を使用して適応法で使用できることを示します。`SRI`と`SRIW1`はわずかに異なる誤差推定器を使用しているため、わずかに異なるステッピング動作を持っています。ノイズラッパーを使用して、同じ2D SDEをどのように異なって解決するかを確認できます：

```julia
prob = SDEProblem(f1, g1, ones(2), (0.0, 1.0))
sol4 = solve(prob, SRI(), abstol = 1e-8, save_noise = true)

W2 = NoiseWrapper(sol4.W)
prob2 = SDEProblem(f1, g1, ones(2), (0.0, 1.0), noise = W2)
sol5 = solve(prob2, SRIW1(), abstol = 1e-8)

using Plots
plot(sol4)
plot!(sol5)
```

![SRI_SRIW1_diff](assets/SRI_SRIW1_diff.png)
