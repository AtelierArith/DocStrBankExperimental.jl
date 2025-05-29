```julia
image_from_paths(tT::TTResult; 
    xresolution::Int=1800, 
    yresolution::Int=1200, 
    xrange = nanextrema(tT.tpointdist), 
    yrange = nanextrema(tT.Tpointdist), 
)
```

`TTResult`を与えられたときのパス密度の2次元画像（ヒストグラム）を生成します。

```julia
julia> imgcounts, xq, yq = image_from_paths(tT; xrange=boundary.agepoints, yrange=boundary.T₀)
```
