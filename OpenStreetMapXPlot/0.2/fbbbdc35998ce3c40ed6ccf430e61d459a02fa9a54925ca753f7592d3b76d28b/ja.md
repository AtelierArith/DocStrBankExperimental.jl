```
plot_nodes!(p, m::OpenStreetMapX.MapData,
    nodeids::Vector{Int};
    start_numbering_from::Union{Int,Nothing}=1,
    km::Bool=false,
    color="darkgreen",
    fontsize=10)
```

ノード識別子 `nodeids` を使用して、プロット `p` にノードをプロットします。デフォルトでは、ノードインデックスがプロットされます（例：1, 2, 3...）。ただし、パラメータ `start_numbering_from` を何も設定しないと、実際のOSMノード識別子が表示されます。`km` パラメータを使用すると、メートルの代わりに地図のキロメートルスケールを持つことができます。

さらなるプロットの更新に使用できるオブジェクトを返します。
