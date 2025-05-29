```julia
minarcdistance(latᵢ,lonᵢ,lat,lon)
```

与えられた点（`latᵢ[i]`,`lonᵢ[i]`）と（`lat`,`lon`）内の任意の点との間の最小の非`NaN`アーク距離（すなわち、弧度での球面上の距離）を、`eachindex(latᵢ, lonᵢ)`の各`i`について返します。

緯度と経度は小数度で指定する必要があります。
