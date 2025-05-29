# DiffEqGPU

[![Join the chat at https://julialang.zulipchat.com #sciml-bridged](https://img.shields.io/static/v1?label=Zulip&message=chat&color=9558b2&labelColor=389826)](https://julialang.zulipchat.com/#narrow/stream/279055-sciml-bridged) [![Global Docs](https://img.shields.io/badge/docs-SciML-blue.svg)](https://docs.sciml.ai/DiffEqGPU/stable/) [![Build status](https://badge.buildkite.com/409ab4d885030062681a444328868d2e8ad117cadc0a7e1424.svg)](https://buildkite.com/julialang/diffeqgpu-dot-jl)

[![codecov](https://codecov.io/gh/SciML/DiffEqGPU.jl/branch/master/graph/badge.svg)](https://codecov.io/gh/SciML/DiffEqGPU.jl)

[![ColPrac: Contributor's Guide on Collaborative Practices for Community Packages](https://img.shields.io/badge/ColPrac-Contributor%27s%20Guide-blueviolet)](https://github.com/SciML/ColPrac) [![SciML Code Style](https://img.shields.io/static/v1?label=code%20style&message=SciML&color=9558b2&labelColor=389826)](https://github.com/SciML/SciMLStyle)

このライブラリは、DifferentialEquations.jlエコシステムのコンポーネントパッケージです。これは、微分方程式ソルバーでGPUを利用するための機能を含んでいます。

## GPUを使用してODEソルバーを加速する2つの方法

GPUを使用してODEソリューションを加速する方法は2つあります。1つは、`u`が非常に大きく、`f`が非常に高価ですが非常に構造化されている場合で、GPUを使用して`f`の計算を加速します。もう1つの使用ケースは、`u`が非常に小さいが、さまざまな初期条件（`u0`）やパラメータ`p`に対してODE `f`を解決したい場合です。その場合、GPUを使用して異なるパラメータや初期条件に対して並列化できます。言い換えれば：

| 問題の種類                | SciMLの解決策                                                                                            |
|:-------------------- |:---------------------------------------------------------------------------------------------------- |
| 大きなODEを加速する          | [CUDA.jlの](https://cuda.juliagpu.org/stable/) CuArrayを`u0`として使用する                                    |
| 多くの`u0`と`p`で同じODEを解く | [DiffEqGPU.jlの](https://docs.sciml.ai/DiffEqGPU/stable/) `EnsembleGPUArray`と`EnsembleGPUKernel`を使用する |

## サポートされているGPU

SciMLのGPUサポートは、以下のような幅広いハードウェアに対応しています：

| GPUメーカー          | GPUカーネル言語 | Juliaサポートパッケージ                                     | バックエンドタイプ                |
|:---------------- |:--------- |:-------------------------------------------------- |:------------------------ |
| NVIDIA           | CUDA      | [CUDA.jl](https://github.com/JuliaGPU/CUDA.jl)     | `CUDA.CUDABackend()`     |
| AMD              | ROCm      | [AMDGPU.jl](https://github.com/JuliaGPU/AMDGPU.jl) | `AMDGPU.ROCBackend()`    |
| Intel            | OneAPI    | [OneAPI.jl](https://github.com/JuliaGPU/oneAPI.jl) | `oneAPI.oneAPIBackend()` |
| Apple (M-Series) | Metal     | [Metal.jl](https://github.com/JuliaGPU/Metal.jl)   | `Metal.MetalBackend()`   |

このチュートリアルでは、NVIDIA GPUのCUDAバックエンドを示しますが、他のGPUもバックエンドの選択を変更することで使用できます。

## メソッド内GPU並列性の例

```julia
using OrdinaryDiffEq, CUDA, LinearAlgebra
u0 = cu(rand(1000))
A = cu(randn(1000, 1000))
f(du, u, p, t) = mul!(du, A, u)
prob = ODEProblem(f, u0, (0.0f0, 1.0f0)) # Float32はGPUでより良い！
sol = solve(prob, Tsit5())
```

## GPUアンサンブルメソッドによるパラメータ並列性の例

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

@time sol = solve(monteprob, GPUTsit5(), EnsembleGPUKernel(CUDA.CUDABackend()),
    trajectories = 10_000, adaptive = false, dt = 0.1f0)
```

## ベンチマーク

私たちの主張に興味がありますか？[https://github.com/utkarsh530/GPUODEBenchmarks](https://github.com/utkarsh530/GPUODEBenchmarks)で、私たちのGPUソルバーとCPUおよびC++、JAX、PyTorchでの実装の比較を確認してください。

## 引用

`DiffEqGPU.jl`を使用している場合は、私たちの論文を引用することを検討してください：

```
@article{utkarsh2024automated,
  title={Automated translation and accelerated solving of differential equations on multiple GPU platforms},
  author={Utkarsh, Utkarsh and Churavy, Valentin and Ma, Yingbo and Besard, Tim and Srisuma, Prakitr and Gymnich, Tim and Gerlach, Adam R and Edelman, Alan and Barbastathis, George and Braatz, Richard D and others},
  journal={Computer Methods in Applied Mechanics and Engineering},
  volume={419},
  pages={116591},
  year={2024},
  publisher={Elsevier}
}
```
