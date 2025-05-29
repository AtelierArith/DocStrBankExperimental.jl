```
make_edge_p_values(lrs::LatticeReactionSystem, make_edge_p_value::Function)
```

格子反応系のためのエッジパラメータ値を生成します。対角隣接のない（直交またはマスクされた）グリッド格子にのみ対応しています。

入力:

  * `lrs`: 値を生成するための格子反応系。

      * `make_edge_p_value`: エッジパラメータ値を生成するためのルールを記述する関数。

出力:     - `ep_vals`: サイズ(num*verts,num*verts)のスパース行列（ここでnum*vertsは`lrs`の頂点の数です）。ここで、`eps[i,j]`は、頂点iから頂点jへのエッジが存在する場合のみ埋められます。`eps[i,j]`の値は`make*edge*p*value`によって決定されます。

ここで、`make_edge_p_value`は、エッジのソースおよびデスティネーション頂点のグリッドインデックスに対応する2つの引数`src_vert`と`dst_vert`を取ります。出力は、そのエッジに割り当てられた単一の値です。

例:     次の例では、頂点(1,1)から頂点(1,2)へのエッジを除いて、すべてのエッジに値`0.1`を割り当て、頂点(1,1)から頂点(1,2)へのエッジには値`1.0`を割り当てます。

```julia
using Catalyst
rn = @reaction_network begin
    (p,d), 0 <--> X
end
tr = @transport_reaction D X
lattice = CartesianGrid((5,5))
lrs = LatticeReactionSystem(rn, [tr], lattice)

function make_edge_p_value(src_vert, dst_vert)
    if src_vert == (1,1) && dst_vert == (1,2)
        return 1.0
    else
        return 0.1
    end
end

D_vals = make_edge_p_values(lrs, make_edge_p_value)
```
