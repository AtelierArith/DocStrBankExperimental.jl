```
hillshade(dem::Matrix{<:Real}; azimuth=315.0, zenith=45.0, cellsize=1.0)
```

hillshadeは、光源の方位角と天頂角が°である場合に、[`傾斜`](@ref)と[`方位`](@ref)に基づいて表面のシミュレートされた照明です。これはBurrough, P. A.、およびMcDonell, R. A.（1998年、地理情報システムの原則）で定義されています。
