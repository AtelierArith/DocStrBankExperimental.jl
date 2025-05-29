```
block_distribution(x_input::AbstractVector; block_size::Integer) = 
    block_distribution(mean, x_input, block_size::Integer)
block_distribution(by::Function, x_input::AbstractVector, block_size::Integer)
```

与えられたデータとブロックサイズに基づいて、各ブロックの特性の推定値の分布を計算します。`BlockDistribution{NBLOCKS}`オブジェクトを返します。ブロックサイズは整数でなければなりません。

# 例

```julia-repl
julia> using MolSimToolkit

julia> x = BlockAverages.test_data(10^7);

julia> d = block_distribution(x; block_size = 25*10^3)
-------------------------------------------------------------------
BlockDistribution{400}
-------------------------------------------------------------------
ブロックの数: 400
推定値: = 0.025151622077551537
平均の標準誤差: 0.05596145099711976
平均の標準偏差: 1.119229019942395
> block_mean には各ブロックのために計算された平均が含まれています。
-------------------------------------------------------------------
```

分布は `d.block_mean` ベクトルに格納され、次のようにプロットできます。

```julia-repl
julia> using Plots

julia> histogram(d)
```
