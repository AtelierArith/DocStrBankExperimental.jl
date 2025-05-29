```
mtp(xae::Vector{U}) where {U <: Number}
```

地球に接近する小惑星の修正されたターゲット平面上のカートesian座標 [地球半径] を返します。

# 引数

  * `xae::Vector{U}`: 接近時の小惑星の地心位置/速度ベクトル [au, au/day].

!!! reference
    https://doi.org/10.1007/s10569-019-9914-4 の15ページの式 (43)-(44) を参照してください。

