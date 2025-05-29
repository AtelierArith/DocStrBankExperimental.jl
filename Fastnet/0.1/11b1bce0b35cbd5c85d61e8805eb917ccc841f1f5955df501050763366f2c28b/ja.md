```
rectlattice!(net::FastNet,dims, <keyword arguments>)
```

与えられた次元 *dims* で長方形の格子を作成します。

*net* のネットワークは、新しいトポロジー、すなわち *dims* で指定された格子に置き換えられます。 *dims* は数値である場合、1D格子に配置されるノードの数を示します。あるいは、*dims* は Int のベクトルである場合もあります。この場合、格子の次元は *dims* の長さと同じであり、*dims* の各要素はこれらの次元の1つにおける格子の長さを指定します。

FastNet が希望するノードまたはリンクの数を収容するのに十分でない場合、引数エラーが発生します。

キーワード引数は次の通りです。

  * periodic : この引数が true の場合、格子はすべての次元で周期境界条件を持つように生成されます。あるいは、*dims* と同じ長さの Bool のベクトルを指定することもできます。この場合、ベクトルの n 番目の引数は、n 番目の次元で格子が周期的であるかどうかを指定します。
  * S : ノードの状態。すべてのノードはこの状態に設定されます。

# 例

```jldoctest
julia> using Fastnet

julia>  net=FastNet(2000,6000,2,[])
Network of 0 nodes and 0 links

julia> rectlattice!(net,[10,20,10],periodic=[true,false,true])
Network of 2000 nodes and 5900 links

julia> degreedist(net)
6-element Vector{Float64}:
 0.0
 0.0
 0.0
 0.0
 0.1
 0.9
```
