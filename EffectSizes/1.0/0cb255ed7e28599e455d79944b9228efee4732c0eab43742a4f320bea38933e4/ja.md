# EffectSizes.jl

[![Stable](https://img.shields.io/badge/docs-stable-blue.svg)](https://harryscholes.github.io/EffectSizes.jl/stable) [![Dev](https://img.shields.io/badge/docs-dev-blue.svg)](https://harryscholes.github.io/EffectSizes.jl/dev) [![Build Status](https://github.com/harryscholes/EffectSizes.jl/workflows/CI/badge.svg)](https://github.com/harryscholes/EffectSizes.jl/actions)

EffectSizes.jlは、効果量の測定のためのJuliaパッケージです。信頼区間は、正規分布を使用するか、ブートストラップ再サンプリングによって効果量に割り当てられます。

このパッケージは、以下の測定のための型を実装しています：

|     **測定** |    **型** |
| ----------:| --------:|
| Cohenの *d* | `CohenD` |
| Hedgeの *g* | `HedgeG` |
| Glassの *Δ* | `GlassΔ` |

## インストール

```jl
julia> import Pkg; Pkg.add("EffectSizes");
```

## 例

```jldoctest
julia> using Random, EffectSizes; Random.seed!(1);

julia> xs = randn(10^3);

julia> ys = randn(10^3) .+ 0.5;

julia> es = CohenD(xs, ys, quantile=0.95); # 正規CI（理想化された分布）

julia> typeof(es)
CohenD{Float64, ConfidenceInterval{Float64}}

julia> effectsize(es)
-0.5035709742336323

julia> quantile(es)
0.95

julia> ci = confint(es);

julia> typeof(ci)
ConfidenceInterval{Float64}

julia> confint(ci)
(-0.5926015897640895, -0.41454035870317507)

julia> es = CohenD(xs, ys, 10^4, quantile=0.95); # ブートストラップCI（経験的分布）

julia> effectsize(es) # 効果量は同じ
-0.5035709742336323

julia> typeof(es)
CohenD{Float64, BootstrapConfidenceInterval{Float64}}

julia> ci = confint(es); # 信頼区間は異なる

julia> lower(ci)
-0.5919535584593746

julia> upper(ci)
-0.4155997394380884
```

## 貢献

アイデアやPRは大歓迎です。
