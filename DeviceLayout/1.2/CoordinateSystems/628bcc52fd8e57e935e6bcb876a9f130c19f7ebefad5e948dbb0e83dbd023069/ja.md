```
mutable struct CoordinateSystem{S<:Coordinate} <: AbstractCoordinateSystem{S}
    name::String
    elements::Vector{GeometryEntity{S}}
    meta::Vector{Meta}
    refs::Vector{GeometryReference}
    create::DateTime

    CoordinateSystem{S}(x, y, ym, z, t) where {S} = new{S}(x, y, ym, z, t)
    CoordinateSystem{S}(x, y, ym, z) where {S} = new{S}(x, y, ym, z, now())
    CoordinateSystem{S}(x, y, ym) where {S} = new{S}(x, y, ym, GeometryReference[], now())
    CoordinateSystem{S}(x) where {S} =
        new{S}(x, GeometryEntity{S}[], Meta[], GeometryReference[], now())
    CoordinateSystem{S}() where {S} = begin
        c = new{S}()
        c.elements = GeometryEntity{S}[]
        c.meta = Meta[]
        c.refs = GeometryReference[]
        c.create = now()
        c
    end
end
```

`CoordinateSystem`は名前を持ち、幾何エンティティ（ポリゴン、長方形）と`GeometryStructure`オブジェクトへの参照を含みます。また、自身の作成時刻を記録します。

要素を追加するには`place!`を使用するか、`CoordinateSystem`と`Cell`の間で無関係であるように`render!`を使用します。参照を追加するには`addref!`または`addarr!`を使用します。
