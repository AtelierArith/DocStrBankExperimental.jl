```julia
mcmc_surface(xaxis::AbstractRange, yaxis::AbstractRange, llmatrix::AbstractMatrix; 
    nsteps::Int=100000, 
    burnin::Int=10000,
)
```

事前に計算された対数尤度面 `llmatrix` を、`xaxis`（水平、列）および `yaxis`（垂直、行）の次元を使用して、マルコフ連鎖モンテカルロアプローチ（メトロポリスアルゴリズム）を用いて x と y の事後分布を計算します。

### 例

```julia
julia> xaxis = yaxis = -5:0.01:5
 -5.0:0.01:5.0

julia> llmatrix = [-((x+1)^2/0.5^2 + (y-1)^2/0.5^2) for y in yaxis, x in xaxis];

julia> xdist, ydist, lldist, acceptancedist = mcmc_surface(xaxis,yaxis,llmatrix);

julia> mean(xdist), std(xdist)
 (-0.9888633375860412, 0.41023499283715603)

julia> mean(ydist), std(ydist)
 (1.0110703489524537, 0.4182564675721746)
```
