```
BayesianPINN(args...; dataset = nothing, kwargs...)
```

`PDESystem`インターフェースのための`discretize`アルゴリズムで、`PDESystem`をHMCベースの事後サンプリングアルゴリズム用の尤度関数に変換します[AdvancedHMC.jl](https://turinglang.org/AdvancedHMC.jl/stable/)。その後、物理インフォームドニューラルネットワーク（PINN）手法を使用してPDEの解の分布を得るために最適化されます。

すべての位置引数とキーワード引数は、以下に示すものを除いて`PhysicsInformedNN`に渡されます。

## キーワード引数

  * `dataset`: 行列のベクトルで、各行列はi番目の従属変数用で、行列の最初の列は従属変数用、残りの列は独立変数用です。逆問題の解決に必要です。
