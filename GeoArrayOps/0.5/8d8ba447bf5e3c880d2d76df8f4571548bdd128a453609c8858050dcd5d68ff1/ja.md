```
multihillshade(dem::Matrix{<:Real}; cellsize=1.0)
```

multihillshadeは、[`slope`](@ref)と[`aspect`](@ref)に基づいて表面のシミュレーションされた照明です。[`hillshade`](@ref)のように、ただし、https://pubs.usgs.gov/of/1992/of92-422/of92-422.pdfで定義された複数のソースを使用しています。GDALの-multidirectionalに似ています。
