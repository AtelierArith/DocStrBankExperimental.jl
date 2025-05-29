```
struct Rectangle{T} <: AbstractPolygon{T}
    ll::Point{T}
    ur::Point{T}
    function Rectangle(a,b)
        # Ensure ll is lower-left, ur is upper-right.
        ll = Point(a.<=b) .* a + Point(b.<=a) .* b
        ur = Point(a.<=b) .* b + Point(b.<=a) .* a
        new(ll,ur)
    end
end
```

A rectangle, defined by opposing lower-left and upper-right corner coordinates. Lower-left and upper-right are guaranteed to be such by the inner constructor.
