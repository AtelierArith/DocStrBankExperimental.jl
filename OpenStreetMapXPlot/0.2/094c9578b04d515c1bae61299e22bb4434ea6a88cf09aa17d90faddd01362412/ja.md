```
addroute!(p, nodes::Dict{Int,T},
               route::Vector{Int};
               route_color::Union{String, Plots.RGB} ="0x000053",
               km::Bool=false,
               start_name="A", end_name="B",
               fontsize=15
               ) where T<:Union{OpenStreetMapX.LLA,OpenStreetMapX.ENU}
```

`route`をプロット`p`に追加し、`nodes`に保存されたノード情報を使用します。

ノードのリスト`route`の最初の要素は`start_name`で注釈が付けられ、最後の要素は`end_name`で注釈が付けられます。`km`パラメータを使用すると、メートルの代わりに地図のキロメートルスケールを持つことができます。

さらなるプロットの更新に使用できるオブジェクトを返します。
