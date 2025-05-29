```julia
nanbinmean(x, y, z, xedges, yedges)
```

`NaN`を無視して、`xedges`と`yedges`で定義されたxとyのビンの2Dグリッドに該当する`z`値の平均を計算します。独立変数`x`と`y`、および従属変数`z`はすべて1Dベクトル（AbstractVectorの任意のサブタイプ）として期待されます。

## 例

```julia
julia> x = y = z = 0.5:9.5;

julia> xedges = yedges = 0:10;

julia> nanbinmean(x,y,z,xedges,yedges)
10×10 Matrix{Float64}:
   0.5  NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN
 NaN      1.5  NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN
 NaN    NaN      2.5  NaN    NaN    NaN    NaN    NaN    NaN    NaN
 NaN    NaN    NaN      3.5  NaN    NaN    NaN    NaN    NaN    NaN
 NaN    NaN    NaN    NaN      4.5  NaN    NaN    NaN    NaN    NaN
 NaN    NaN    NaN    NaN    NaN      5.5  NaN    NaN    NaN    NaN
 NaN    NaN    NaN    NaN    NaN    NaN      6.5  NaN    NaN    NaN
 NaN    NaN    NaN    NaN    NaN    NaN    NaN      7.5  NaN    NaN
 NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN      8.5  NaN
 NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN    NaN      9.5
```
