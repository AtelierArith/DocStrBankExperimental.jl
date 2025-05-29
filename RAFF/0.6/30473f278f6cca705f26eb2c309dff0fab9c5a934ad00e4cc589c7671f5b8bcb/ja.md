```
generate_noisy_data(model::Function, n::Int, np::Int, p::Int;
    x_interval::Tuple{Float64, Float64}=(-10.0, 10.0),
    θSol::Vector{Float64}=10.0 * randn(Float64, n),
    std::Float64=200.0, out_times::Float64=7.0)

generate_noisy_data(model::Function, n::Int, np::Int, p::Int,
    x_interval::Tuple{Float64, Float64})

generate_noisy_data(model::Function, n::Int, np::Int, p::Int,
    θSol::Vector{Float64}, x_interval::Tuple{Float64, Float64})
```

ランダムにフィッティングする1次元データ問題を生成します。

この関数は、`model(x, θ)`関数、パラメータの数`n`、生成するポイントの数`np`、および信頼できるポイントの数`p`を受け取ります。

もし`n`次元ベクトル`θSol`が提供されると、正確な解はランダムに生成されません。値を評価するために`model`を生成するための区間`[xMin, xMax]`（*非推奨*）または`x_interval`も提供できます。

戻り値はタプル`(data, θSol, outliers)`であり、ここで

  * `data`: (`np` x `3`) 配列で、各行には`x`と`model(x, θSol)`が含まれます。
  * `θSol`: 正確な解を持つ`n`次元ベクトル。
  * `outliers`: このデータセットの外れ値。
