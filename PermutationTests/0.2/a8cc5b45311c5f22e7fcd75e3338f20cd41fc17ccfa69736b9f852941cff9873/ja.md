```julia
function statistic(x::UniData, y::UniData, stat::PearsonR; 
                standardized::Bool=false, 
                centered::Bool=false, 
                means::Tuple=(), 
                sds::Tuple=(), kwargs...)
```

入力データベクトル `x` と `y` のピアソン積モーメント相関 *r* 統計量。

`x` と `y` の平均および/または標準偏差がそれぞれタプル `means` と `sds` として渡される場合、それらは計算されません。

`centered` が true の場合、2つのベクトルはゼロ平均を持つと仮定されます。

`standardized` が true の場合、x と y は標準化されていると仮定されるため、交差積のみを計算する必要があります。この関数が同じデータ入力ベクトルに対して繰り返し呼び出され、データの置換による p 値を計算する場合、交差積はピアソン相関の標準化されたデータに対する同等の検定統計量であるため、これが最も効率的な方法です。

*例*

```julia
using PermutationTests
x, y = randn(10), randn(10);
c1 = statistic(x, y, PearsonR())

zx=μ0σ1(x);
zy=μ0σ1(y);
c2 = statistic(zx, zy, PearsonR(); standardized=true)
```

[`μ0σ1`](@ref) を参照してください。
