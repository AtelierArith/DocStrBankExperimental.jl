```
struct Rectangle{T} <: AbstractPolygon{T}
    ll::Point{T}
    ur::Point{T}
    function Rectangle(a,b)
        # llが左下、urが右上であることを保証します。
        ll = Point(a.<=b) .* a + Point(b.<=a) .* b
        ur = Point(a.<=b) .* b + Point(b.<=a) .* a
        new(ll,ur)
    end
end
```

対角にある左下と右上のコーナー座標によって定義される長方形。左下と右上は内部コンストラクタによってそのように保証されています。
