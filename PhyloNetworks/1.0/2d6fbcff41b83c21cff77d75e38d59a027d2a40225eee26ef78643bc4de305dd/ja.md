```
vcv(net::HybridNetwork; model::AbstractString="BM",
                        corr::Bool=false,
                        checkpreorder::Bool=true)
```

この関数は、特性進化のブラウン運動モデルを仮定して、ネットワークのティップ間の分散共分散行列を計算します（単位分散）。オプション引数 `corr` が `true` に設定されている場合、相関行列が返されます。

この関数は、ネットワークのティップによって名前付けされた列を持つ `DataFrame` オブジェクトを返します。

共分散行列の計算には、ノードの事前順序付けが必要です。`checkpreorder` が true（デフォルト）である場合、ネットワークに対して [`preorder!`](@ref) が事前に実行されます。そうでない場合、ネットワークはすでに事前順序であると仮定されます。

この関数は内部的に [`sharedpathmatrix`](@ref) を呼び出し、ネットワークのすべてのノード間の分散行列を計算します。

# 例

```jldoctest
julia> tree_str = "(((t2:0.14,t4:0.33):0.59,t3:0.96):0.14,(t5:0.70,t1:0.18):0.90);";

julia> tree = readnewick(tree_str);

julia> C = vcv(tree)
5×5 DataFrame
 Row │ t2       t4       t3       t5       t1      
     │ Float64  Float64  Float64  Float64  Float64 
─────┼─────────────────────────────────────────────
   1 │    0.87     0.73     0.14      0.0     0.0
   2 │    0.73     1.06     0.14      0.0     0.0
   3 │    0.14     0.14     1.1       0.0     0.0
   4 │    0.0      0.0      0.0       1.6     0.9
   5 │    0.0      0.0      0.0       0.9     1.08

```

次のブロックは `ape` がインストールされている必要があります（実行しないでください）：

```julia
julia> using RCall # ape vcv 関数との比較

julia> R"ape::vcv(ape::read.tree(text = $tree_str))"
RCall.RObject{RCall.RealSxp}
     t2   t4   t3  t5   t1
t2 0.87 0.73 0.14 0.0 0.00
t4 0.73 1.06 0.14 0.0 0.00
t3 0.14 0.14 1.10 0.0 0.00
t5 0.00 0.00 0.00 1.6 0.90
t1 0.00 0.00 0.00 0.9 1.08

```

共分散はネットワーク上でも計算できます（モデルについてはBastide et al. 2018を参照）。

```jldoctest
julia> net = readnewick("((t1:1.0,#H1:0.1::0.30):0.5,((t2:0.9)#H1:0.2::0.70,t3:1.1):0.4);");

julia> C = vcv(net)
3×3 DataFrame
 Row │ t1       t2       t3      
     │ Float64  Float64  Float64 
─────┼───────────────────────────
   1 │    1.5     0.15      0.0
   2 │    0.15    1.248     0.28
   3 │    0.0     0.28      1.5
```
