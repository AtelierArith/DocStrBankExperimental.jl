```julia
image_from_paths(xpoints::AbstractMatrix, ypoints::AbstractMatrix; 
    xresolution::Int=1800, 
    yresolution::Int=1200, 
    xrange=nanextrema(xpoints), 
    yrange=nanextrema(ypoints),
)
```

与えられた一連の x-y 点を列ごとに別々の行列 `xpoints` と `ypoints` に格納して、パス密度の 2d 画像（ヒストグラム）を生成します。`x` は独立変数であると仮定されます（すなわち、x-y 点は `x` の増加順にプロットされます）。

### 例

```julia
julia> nsims = 1000
1000

julia> xdist = rand(10, nsims);

julia> ydist = rand(10, nsims);

julia> imgcounts, xbincenters, ybincenters = image_from_paths(xpaths, ypaths; xresolution=50, yresolution=50)
([8 15 … 9 11; 12 4 … 14 11; … ; 9 15 … 9 9; 10 17 … 10 14], -3.715247394908744:0.1523101612461508:3.747950506152645, -3.86556932981587:0.1497772964483582:3.4735181961536803)
```
