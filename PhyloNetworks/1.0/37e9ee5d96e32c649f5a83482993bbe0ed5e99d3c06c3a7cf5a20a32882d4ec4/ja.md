```
nni!([rng::AbstractRNG,]
     net::HybridNetwork,
     e::Edge,
     nohybridladder::Bool=true,
     no3cycle::Bool=true,
     constraints::Vector{TopologyConstraint}=TopologyConstraint[]
)
```

エッジ `e` の周りで最近傍隣接交換 (NNI) を実行し、制約を満たすすべての可能なNNIの中からランダムに選択します（例えば、3つ、場合によっては `e` に応じてそれ以上）。新しいネットワークはDAGである必要があります。エッジの親/子ノードがツリーまたはハイブリッドノードであるかどうかに応じて、エッジの周りの可能なNNI移動の数が決まります。これは [`nnimax`](@ref) によって計算されます。

オプション `no3cycle` は、ネットワーク内に3サイクルを生成する移動を禁止します。`no3cycle` = false の場合、2サイクルおよび3サイクルが生成される可能性があります。

デフォルト値は位置引数（キーワード引数ではない）用であるため、2つ以上の引数を使用できますが、特定の順序で使用する必要があります： `nni!(net, e)` または `nni!(net, e, nohybridladder)`、`nni!(net, e, nohybridladder, no3cycle)`、`nni!(net, e, nohybridladder, no3cycle, contraints)`。

前提条件：

  * 開始ネットワークには3サイクルがないこと、`no3cycle=true` の場合。入力ネットワーク内の2サイクルおよび3サイクルの存在をチェックしません。
  * エッジのフィールド `ischild1` は入力ネットワーク内で正しいこと。（このフィールドは出力ネットワーク内で正しくなります。）

出力：移動を元に戻す方法を示す情報、またはすべてのNNIが失敗した場合は `nothing`。

# 例

```jldoctest
julia> str_network = "(((S8,S9),(((((S1,S2,S3),S4),(S5)#H1),(#H1,(S6,S7))))#H2),(#H2,S10));";

julia> net = readnewick(str_network);

julia> # using Random; Random.seed!(3); ## doctestの再現性のためにコメントアウトされていますが、ユーザーはこの行を使用して分析でシードを設定できます。

julia> undoinfo = nni!(net, net.edge[3], true, true); # trueはハイブリッドラダーと3サイクルを避けるため
```

次の例では、安定したRNGを使用して、例をJuliaのバージョン間で再現可能にします。ただし、この特定のRNGは*推奨されていません*。デフォルトで使用されるRNGの方が優れています（例えば、はるかに効率的です）。

```jldoctest nni
julia> str_network = "(((S8,S9),(((((S1,S2,S3),S4),(S5)#H1),(#H1,(S6,S7))))#H2),(#H2,S10));";

julia> net = readnewick(str_network);

julia> # using Pkg; Pkg.add("StableRNGs") # StableRNGsをまだインストールしていない場合はインストールするため

julia> using StableRNGs

julia> rng = StableRNG(791);

julia> undoinfo = nni!(rng, net, net.edge[3], true, true); # trueはハイブリッドラダーと3サイクルを避けるため

julia> writenewick(net)
"((S9,((((((S1,S2,S3),S4),(S5)#H1),(#H1,(S6,S7))))#H2,S8)),(#H2,S10));"

julia> nni!(undoinfo...);

julia> writenewick(net) == str_network # netが元のトポロジーに戻る：NNIが「元に戻された」
true
```
