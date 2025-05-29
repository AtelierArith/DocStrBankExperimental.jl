```
tdist(a,b) -> Number
```

点 `a` と `b` の間の「トンネル距離」を計算します。

トンネル距離はユークリッド空間における直線距離、すなわち `norm(ECEF(a) - ECEF(b))` です。

`a` と `b` は次のいずれかである可能性があります：

  * 南北および東西の座標のペア。
  * 二次元座標。
  * 上記のいずれかに追加の高度があるもの。

# 例

```jldoctest
julia> tdist(EastNorth(0,0), EastNorth(3,4))
5.0000000000001075

julia> tdist(EastNorth(0,0), (EastNorth(3,0), Alt(4)))
5.0000005648476336

julia> tdist(EastNorth(0,0), (East(3), North(0), Alt(4)))
5.0000005648476336
```
