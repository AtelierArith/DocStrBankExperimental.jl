```
getnodeheights(net, checkpreorder::Bool=true)
getnodeheights!(net, checkpreorder::Bool=true)
```

ノードの高さのベクトル、すなわち、各ノードからルートまでの距離。ネットワークが時間的一貫性を持たない場合、エラーがスローされます。ネットワークが時間的一貫性を持つとは、任意のノード `v` に対して、ルートから `v` までのすべてのパスが同じ長さであることを意味します。（この条件はハイブリッドノードで確認するだけで十分です）。ウルトラメトリック性は仮定されていません：ティップはすべてルートから同じ距離にある必要はありません。`checkpreorder=false` の場合、ネットワークはすでに [`preorder!`](@ref) で前順に並べられていると仮定します。

ツリーエッジに欠落した長さ（-1としてコーディングされている）がある場合、両方の関数はエラーをスローします。一般に、ネットワークを時間的一貫性に保つためにツリーエッジの長さを割り当てる方法は指数関数的に多く存在する可能性があります。

`getnodeheights` は、欠落したハイブリッドエッジの長さを見つけた際に警告を送信し、その他は `getnodeheights!` と同様に進行しますが、ネットワークを変更することはありません。`getnodeheights!` は、ネットワークを時間的一貫性に保つために、欠落した長さに値を割り当てることを試みます（ハイブリッドエッジのみ）。

ハイブリッドエッジ `e` に欠落した長さがある場合、`getnodeheights!` はその子ハイブリッドノード `h` で次のように進行します：

  * `h` のすべての親エッジが長さを欠いている場合：最短の非負の長さが割り当てられ、`h` でネットワークが時間的一貫性を持つようにします。特に、パートナーエッジの一つに長さ0が割り当てられ、`h` はできるだけ古く、すなわち、できるだけルートに近くなります：リティキュレーションは「ジップアップ」されます。
  * それ以外の場合：エッジ `e` の長さは、パートナーエッジの長さに基づいて、`h` でネットワークが時間的一貫性を持つようにする唯一の値に設定されます。この値が負の場合、エラーがスローされます。

出力：ノードの高さのベクトル、各ノードごとに、`net.vec_node` と同じ順序で。

他にも、[`istimeconsistent`](@ref) および [`getnodeheights_average`](@ref) を参照してください。

例：

```jldoctest
julia> net = readnewick("(((C:1,(A:1)#H1:1.5::0.7):1,(#H1:0.3::0.3,E:2.0):2.2):1.0,O:5.2)root;");

julia> # using PhyloPlots; plot(net, useedgelength=true, showedgelength=true, shownodenumber=true); # to see

julia> nodeheight = getnodeheights(net)
9-element Vector{Float64}:
 0.0
 5.2
 1.0
 3.2
 5.2
 2.0
 3.5
 4.5
 3.0

julia> [node.number => (height, node.name) for (height,node) in zip(nodeheight, net.vec_node)]
9-element Vector{Pair{Int64, Tuple{Float64, String}}}:
 -2 => (0.0, "root")
  5 => (5.2, "O")
 -3 => (1.0, "")
 -6 => (3.2, "")
  4 => (5.2, "E")
 -4 => (2.0, "")
  3 => (3.5, "H1")
  2 => (4.5, "A")
  1 => (3.0, "C")

```
