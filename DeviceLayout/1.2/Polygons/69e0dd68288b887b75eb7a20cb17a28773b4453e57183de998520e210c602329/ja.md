```
struct Ellipse{T} <: GeometryEntity{T}
    center::Point{T}
    radii::NTuple{2, T}
    angle::typeof(1.0°)
    Ellipse{T}(c, r, a) where {T} = new{T}(c, r[1] < r[2] ? (r[2], r[1]) : r, a)
end
Ellipse(center::Point{T}, radii, angle) where {T} = Ellipse{T}(center, radii, angle)
Ellipse(center::Point{T}; r::T) where {T} = Ellipse{T}(center, (r, r), 0.0°)
```

重心、半径、および主軸角を持つ楕円を表します。主軸の半径は半径内で最初に格納され、軸の角度はx軸から定義されます。
