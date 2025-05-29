# Logistics.jl

[![Documentation](https://img.shields.io/badge/docs-stable-blue.svg)](https://Mikumikunisiteageru.github.io/Logistics.jl/stable) [![Documentation](https://img.shields.io/badge/docs-dev-blue.svg)](https://Mikumikunisiteageru.github.io/Logistics.jl/dev) [![CI](https://github.com/Mikumikunisiteageru/Logistics.jl/actions/workflows/CI.yml/badge.svg)](https://github.com/Mikumikunisiteageru/Logistics.jl/actions/workflows/CI.yml) [![Codecov](https://codecov.io/gh/Mikumikunisiteageru/Logistics.jl/branch/main/graph/badge.svg)](https://codecov.io/gh/Mikumikunisiteageru/Logistics.jl) [![Aqua.jl Quality Assurance](https://img.shields.io/badge/Aquajl-%F0%9F%8C%A2-aqua.svg)](https://github.com/JuliaTesting/Aqua.jl)

Logistics.jl は、$[0, 1]$ の実数（例：確率）を表すデータ型 `Logistic` を定義し、より数値的に安定した算術演算を提供します。

## 例

以下は、このパッケージの使用法を示すいくつかの簡単な例です。Logistics.jl の詳細については、[ドキュメント](https://Mikumikunisiteageru.github.io/Logistics.jl/)をご覧ください。

```julia
julia> using Logistics

julia> x = Logistic(0)
Logistic{Float64}(0.0) ≈ 0.5

julia> y = logisticate(0.2)
Logistic{Float64}(-1.3862943611198906) ≈ 0.2

julia> x + y
Logistic{Float64}(0.8472978603872037) ≈ 0.7

julia> x - y
Logistic{Float64}(-0.8472978603872037) ≈ 0.3

julia> x * y
Logistic{Float64}(-2.197224577336219) ≈ 0.10000000000000002

julia> y / x
Logistic{Float64}(-0.40546510810816444) ≈ 0.4

julia> x ^ 2
Logistic{Float64}(-1.0986122886681098) ≈ 0.25

julia> mx = x ^ 10000
Logistic{Float64}(-6931.471805599453) ≈ 0.0

julia> my = y ^ 4307
Logistic{Float64}(-6931.84908885367) ≈ 0.0

julia> mx + my
Logistic{Float64}(-6930.949611751832) ≈ 0.0

julia> mx - my
Logistic{Float64}(-6932.629282338215) ≈ 0.0

julia> mx * my
Logistic{Float64}(-13863.320894453122) ≈ 0.0

julia> mx \ my
Logistic{Float64}(0.7801934845449816) ≈ 0.6857218127893691

julia> sqrt(mx)
Logistic{Float64}(-3465.7359027997263) ≈ 0.0

julia> cbrt(mx)
Logistic{Float64}(-2310.490601866484) ≈ 0.0

julia> log(y)
-1.6094379124341003

julia> logit(y)
-1.3862943611198906
```
