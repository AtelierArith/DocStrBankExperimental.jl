```
make_directed_edge_values(lrs::LatticeReactionSystem, x_vals::Tuple{T,T}, y_vals::Tuple{T,T} = (undef,undef),
                 z_vals::Tuple{T,T} = (undef,undef)) where {T}
```

ラティス反応系のためのエッジパラメータ値を生成します。対角隣接のない（直交またはマスクされた）グリッドラティスにのみ対応しています。各次元（x、場合によってはyおよびz）と方向には、それぞれの定数エッジパラメータ値が割り当てられています。

入力:     - `lrs`: 値を生成するラティス反応系。     - `x_vals::Tuple{T,T}`: x次元に沿った増加（低いxインデックスから高いxインデックスへ）および減少（高いxインデックスから低いxインデックスへ）方向の値。     - `y_vals::Tuple{T,T}`: y次元に沿った増加および減少方向の値。2次元および3次元グリッドでのみ使用する必要があります。     - `z_vals::Tuple{T,T}`: z次元に沿った増加および減少方向の値。3次元グリッドでのみ使用する必要があります。

出力:     - `ep_vals`: サイズ(num*verts,num*verts)のスパース行列（ここでnum*vertsは`lrs`の頂点の数）。ここで、`eps[i,j]`は、頂点iから頂点jへのエッジが存在する場合にのみ埋められます。`eps[i,j]`の値は、`x*vals`、`y*vals`、および`z*vals`のタプルと、グリッド内の頂点iとjの相対位置によって決まります。

隣接する2つの頂点は、常に正確に1つの次元（x、y、またはz）で異なることに注意する必要があります。対応するタプルがどの値が割り当てられるかを決定します。

例:     次の例では、x次元で拡散を持ちたいが、低いy値から高いy値への一定の流れ（高いyから低いyへの輸送ではない）を持ちたいと考えています。次の方法でそれを達成します：

```julia
using Catalyst
rn = @reaction_network begin
    (p,d), 0 <--> X
end
tr = @transport_reaction D X
lattice = CartesianGrid((5,5))
lrs = LatticeReactionSystem(rn, [tr], lattice)

D_vals = make_directed_edge_values(lrs, (0.1, 0.1), (0.1, 0.0))
```

ここでは、2次元グリッドがあるため、`make_directed_edge_values`に最初の2つのタプルのみを提供します。
