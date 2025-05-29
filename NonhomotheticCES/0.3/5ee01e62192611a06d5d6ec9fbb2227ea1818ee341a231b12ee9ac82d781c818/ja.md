# NonhomotheticCES.jl

![lifecycle](https://img.shields.io/badge/lifecycle-experimental-orange.svg) [![build](https://github.com/tpapp/NonhomotheticCES.jl/workflows/CI/badge.svg)](https://github.com/tpapp/NonhomotheticCES.jl/actions?query=workflow%3ACI) [![codecov.io](http://codecov.io/github/tpapp/NonhomotheticCES.jl/coverage.svg?branch=master)](http://codecov.io/github/tpapp/NonhomotheticCES.jl?branch=master)

非同次CES好みの消費集約器を解くための小さなパッケージです。詳細は以下の文献を参照してください。

*Comin, D., Lashkari, D., & Mestieri, Martí (2021). Structural change with long-run income and price effects. Econometrica, 89(1), 311–374.*

## API

```julia
using NonhomotheticCES, StaticArrays

U = NonhomotheticCESUtility(σ,  # σ
                            Ω̂s, # LOG sectoral Ωs
                            ϵs) # sectoral ϵs

Ĉ = log_consumption_aggregator(U,
                               p̂s, # LOG prices
                               Ê)  # LOG expenditure

ĉs = log_sectoral_consumptions(U, p̂s, Ê, Ĉ)
```

APIは良好な初期推定値を用いたニュートンソルバーを使用しており、**固定されたステップ数**で結果の滑らかさを助けています（精度のコストがかかります）。もし本当に、最後の[ulp](https://en.wikipedia.org/wiki/Unit_in_the_last_place)までの精度が必要な場合は、もっと多くのステップを使用してください。

部分適用バージョンもあり、デフォルトで後のニュートンステップを少なくして、さらに良い初期推定値を計算します：

```julia
A = log_consumption_aggregator(U, p̂s)
Ĉ = A(Ê)
```

詳細についてはドキュメントストリングを参照してください。

## Integrations

部分導関数はADフレームワークに実装されています：

1. [X] [ForwardDiff.jl](https://github.com/JuliaDiff/ForwardDiff.jl)
2. [ ] [ChainRulesCore.jl](https://github.com/JuliaDiff/ChainRulesCore.jl) **WIP**

## Example

σ = 0.5, Ω̂₁ = 0.0, Ω̂₂ = 0.0, ϵ₁ = 1.0, ϵ₂ = 2.0, p̂₁ = 0.1, p̂₂ = 0.0 (see [script/plot.jl](./script/plot.jl)).

<img src="script/example.png" width="50%">
