```
lmlovo(model::Function [, θ::Vector{Float64} = zeros(n)], data::Array{Float64, 2},
       n::Int, p::Int [; kwargs...])

lmlovo(model::Function, gmodel!::Function [, θ::Vector{Float64} = zeros(n)],
       data::Array{Float64,2}, n::Int, p::Int [; MAXITER::Int=200,
       ε::Float64=10.0^-4])
```

`n`パラメータモデル`model`を行列`data`で与えられたデータにフィットさせます。この戦略はLOVO関数に基づいており、`p`（0 < `p` <= `data`の行数）点のみが信頼されます。このバージョンではLevenberg-Marquardtアルゴリズムが実装されています。

行列`data`はフィットさせるデータです。この行列は以下の形式である必要があります。

```
x11 x12 ... x1N y1
x21 x22 ... x2N y2
:
```

ここで`N`はモデルの引数の次元（すなわち`x`の次元）です。

`θ`が提供されている場合、それは出発点として使用されます。

関数`model`のシグネチャは以下のように指定されるべきです。

```
model(x::Union{Vector{Float64}, SubArray}, θ::Vector{Float64})
```

ここで`x`は変数で、`θ`は`n`次元のパラメータベクトルです。モデルの勾配`gmodel!`が提供されていない場合、

```
gmodel! = (g::SubArray, x::Union{Vector{Float64}, SubArray},
           θ::Vector{Float64})
```

`ForwardDiff.gradient!`が呼び出されて計算されます。**注意**：この選択はアルゴリズムの計算性能に影響を与えます。さらに、`ForwardDiff.jl`が使用されている場合、関数`model`からベクトル`θ`のシグネチャを**削除する必要があります**。

オプションの引数は次のとおりです。

  * `MAXITER`: 最大反復回数
  * `ε`: 関数の勾配の許容誤差

[`RAFFOutput`](@ref)オブジェクトを返します。
