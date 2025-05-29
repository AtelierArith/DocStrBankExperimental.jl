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

Represent an ellipse with a centroid, radii and major axis angle. The major axis radius is stored first within radii, and the axis angle is defined from the x-axis.
