```
NVModel(demand, cost, price, salvage=0)
```

ユニット `cost`、ユニット販売 `price`、および `demand` 分布を持つ [Newsvendor モデル](https://en.wikipedia.org/wiki/Newsvendor_model) をキャプチャします。需要は、パッケージ [Distributions.jl](https://juliastats.org/Distributions.jl/latest/univariate/) からの任意の一変量分布である可能性があります。

# 例

```julia-repl
julia> using Distributions
```

```jldoctest nvm; setup = :(using Distributions, NewsvendorModel)
julia> nvm = NVModel(demand = Normal(50, 20), cost = 5, price = 7)
Data of the Newsvendor Model
 * Demand distribution: Normal{Float64}(μ=50.0, σ=20.0)
 * Unit cost: 5.00
 * Unit selling price: 7.00
```

これは、ユニットコスト 5 およびユニット価格 7 のモデルを定義し、不確実な需要が平均 50 および標準偏差 20 の正規分布から引き出されることを示しています。

オプションのキーワード引数とそのデフォルト：

```
NVModel(demand [; kwargs])
```

  * ユニットあたりの `cost`；デフォルトは `0.0`
  * ユニットあたりの販売 `price`；デフォルトは `0.0`
  * 残りのユニットから得られる `salvage` 値；デフォルトは `0.0`
  * 残りのユニットによって引き起こされる `holding` コスト、例えば、追加の資本コストや倉庫コスト；本質的には負の廃棄値；デフォルトは `0.0`
  * ユニットが不足している場合の `backorder` 罰金、例えば、納品目標を逃した場合の契約上の罰金や、未提供の顧客の将来の利益を逃した場合の罰金；デフォルトは `0.0`
  * 未提供の顧客に代替品を販売することによって得られる `substitute` 利益、例えば、別の製品を販売する場合や将来にサービスを提供する場合；本質的には負のバックオーダー罰金；デフォルトは `0.0`
  * 操作の固定コスト `fixcost`；デフォルトは `0.0`
  * 最小実行可能数量 `q_min`、例えば、生産制限による；非負でなければならない；デフォルトは `0`
  * 最大実行可能数量 `q_max`、例えば、生産制限による；`q_min` 以上でなければならない；デフォルトは `Inf`

# 例

ユニットコスト 5、ユニット価格 7、需要が 50 から 80 の間の一様分布であり、ユニットの廃棄が 0.5 で、バックオーダーがユニットあたり 2 の罰金で、操作に固定コスト 100 がかかるニュースベンダー問題を次のように定義します：

```jldoctest nvm
julia> nvm2 = NVModel(demand = Uniform(50, 80), cost = 5, price = 7, salvage = 0.5, backorder = 2, fixcost = 100)
Data of the Newsvendor Model
 * Demand distribution: Uniform{Float64}(a=50.0, b=80.0)
 * Unit cost: 5.00
 * Unit selling price: 7.00
 * Unit salvage value: 0.50
 * Unit backorder penalty: 2.00
 * Fixed cost: 100.00
```

需要は、最初にキーワードなしで渡すことができる必要な引数であることに注意してください。さらに、デフォルトと異なる値のみが表示されます。

ユニットコスト 5、ユニット価格 7、需要が 50 から 80 の間の一様分布であり、ユニットの廃棄が 0.5 で、バックオーダーがユニットあたり 2 の罰金で、操作に固定コスト 100 がかかるニュースベンダー問題を次のように定義します：

```jldoctest nvm
julia> nvm3 = NVModel(Uniform(50, 80), 5, 7, 0.5, backorder = 2, fixcost = 100, q_min=0)
Data of the Newsvendor Model
 * Demand distribution: Uniform{Float64}(a=50.0, b=80.0)
 * Unit cost: 5.00
 * Unit selling price: 7.00
 * Unit salvage value: 0.50
 * Unit backorder penalty: 2.00
 * Fixed cost: 100.00
julia> nvm3 == nvm2
true
```

ホールディングコストは本質的に過剰コストです。バックオーダー罰金は本質的に不足コストです。ビールゲームではホールディングコストが 0.5 USD で、バックログコストがユニットあたり 1 USD です。需要は 0 から 300 の間で一様であると仮定されています。

```jldoctest nvm
julia> beer = NVModel(Uniform(0, 300), backorder = 1, holding = 0.5)
Data of the Newsvendor Model
 * Demand distribution: Uniform{Float64}(a=0.0, b=300.0)
 * Unit cost: 0.00
 * Unit selling price: 0.00
 * Unit holding cost: 0.50
 * Unit backorder penalty: 1.00
```
