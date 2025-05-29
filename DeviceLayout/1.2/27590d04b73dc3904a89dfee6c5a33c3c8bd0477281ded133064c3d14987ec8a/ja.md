```
mutable struct ArrayReference{S,T} <: GeometryReference{S,T}
    structure::T
    origin::Point{S}
    deltacol::Point{S}
    deltarow::Point{S}
    col::Int
    row::Int
    xrefl::Bool
    mag::Float64
    rot::Float64
end
```

`origin`から始まる`row`行`col`列の`structure`の配列で、ベクトル`deltacol`と`deltarow`によって広がっています。配列全体に対してオプションのx反射`xrefl`、拡大率`mag`、および回転角度`rot`があります。単位なしで角度が与えられた場合、それはラジアンであると見なされます。

型変数`T`は循環定義を避けるためのものです。
