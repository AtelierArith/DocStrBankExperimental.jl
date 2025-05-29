```
CompositeModel(components;
gas = BasicIdeal,
liquid = RackettLiquid,
saturation = LeeKeslerSat,
gas_userlocations = String[],
liquid_userlocations = String[],
saturation_userlocations = String[],
mapping = nothing,
reference_state = nothing,
verbose = false)
```

流体（および/または固体）の表現を保持するモデルで、ライブラリの残りの部分で使用されるヘルモルツエネルギーに基づくアプローチを使用して評価されません。

「流体」と「固体」のフィールドが含まれています。流体のために利用可能な表現は3つあります：

  * ヘルモルツに基づくEoS
  * 流体相関、ガスモデル、飽和圧力を取得するための相関、および液体モデルで構成されています。ガスモデルと液体モデルはオプションでヘルモルツモデルにもできますが、飽和液体と蒸気のための相関も許可されています。
  * 活動モデル、液体活動と流体のモデルで構成されています。流体モデルはヘルモルツに基づくモデル、または相関を含む別の`CompositeModel`であることができます。

固体フィールドが指定されると、いくつかの特性（`volume`など）が計算において固体相を考慮し始めます。オプションで、SLE平衡のための特定の相関を提供する他のモデル（`SolidHfus`など）があります。

## 例：

  * 相関を使用して計算された飽和圧力：

```julia-repl
#液体のためのラックット相関、飽和圧力のためのDIPPR 101相関、蒸気体積のための理想気体
julia> model = CompositeModel(["water"],liquid = RackettLiquid,saturation = DIPPR101Sat,gas = BasicIdeal)
Composite Model (Correlation-Based) with 1 component:
 Gas Model: BasicIdeal()
 Liquid Model: RackettLiquid("water")
 Saturation Model: DIPPR101Sat("water")

julia> saturation_pressure(model,373.15)
(101260.56298096628, 1.8234039042643886e-5, 0.030639190960720403)
```

  * 流体相関とラウルトソルバーを使用して計算されたバブル圧力：

```julia-repl
julia> model = CompositeModel(["octane","heptane"],liquid = RackettLiquid,saturation = DIPPR101Sat,gas = BasicIdeal)
Composite Model (Correlation-Based) with 2 components:
 Gas Model: BasicIdeal()
 Liquid Model: RackettLiquid("octane", "heptane")
 Saturation Model: DIPPR101Sat("octane", "heptane")

julia> bubble_pressure(model,300.15,[0.9,0.1])
(2552.3661540464022, 0.00015684158726046333, 0.9777538974501402, [0.7376170278676232, 0.2623829721323768])
```

  * 流体特性のための別のモデルとともに活動モデルを使用したバブル圧力：

```julia-repl
#ヘルモルツに基づく流体を使用
julia> model = CompositeModel(["octane","heptane"],liquid = UNIFAC,fluid = PR)
Composite Model (γ-ϕ) with 2 components:
 Activity Model: UNIFAC{PR{BasicIdeal, PRAlpha, NoTranslation, vdW1fRule}}("octane", "heptane")
 Fluid Model: PR{BasicIdeal, PRAlpha, NoTranslation, vdW1fRule}("octane", "heptane")

julia> bubble_pressure(model,300.15,[0.9,0.1])
(2694.150594740186, 0.00016898441224336215, 0.9239727973658585, [0.7407077952279438, 0.2592922047720562])

#相関に基づく流体を使用
julia> fluidmodel = CompositeModel(["octane","heptane"],liquid = RackettLiquid,saturation = DIPPR101Sat,gas = BasicIdeal);
model2 = CompositeModel(["octane","heptane"],liquid = UNIFAC, fluid = fluidmodel)
Composite Model (γ-ϕ) with 2 components:
 Activity Model: UNIFAC{PR{BasicIdeal, PRAlpha, NoTranslation, vdW1fRule}}("octane", "heptane")
 Fluid Model: FluidCorrelation{BasicIdeal, RackettLiquid, DIPPR101Sat}("octane", "heptane")

julia> bubble_pressure(model2,300.15,[0.9,0.1])
(2551.6008524130893, 0.00015684158726046333, 0.9780471551726359, [0.7378273929683233, 0.2621726070316766])
```
