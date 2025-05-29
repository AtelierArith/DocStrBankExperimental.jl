```
Atom(name::Symbol, element::Element, position_cart::Point3{Length}, position_cryst::Point3;
     pseudo::String = "",
     projections::Vector{Projection} = Projection[],
     magnetization::Vec3 = Vec3(0.0, 0.0, 0.0),
     dftu::DFTU = DFTU())
```

`atom`の表現。

`atom`の`name`は、`pseudo`、`projections`、`magnetization`および[`dftu`](@ref DFTU)属性が同じである原子が同じタイプに属するという意味で、`atom`タイプの識別子として使用されます。これは、同じタイプでない原子には異なる名前が付けられることを意味します。このようにする理由は、同じ種類のすべての原子のこれらのパラメータを同時に変更することがしばしば意味を持つ一方で、個々の原子に対してそれらを変更する柔軟性も許可するためです。

`position_cart`は、`Ang`のような有効な`Unitful.Length`型である必要があります。

この属性に関する詳細情報については、[`Element`](@ref)のドキュメントを参照してください。
