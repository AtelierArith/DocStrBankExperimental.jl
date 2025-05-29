```
rand([rng::AbstractRNG,]
      net::HybridNetwork,
      params::ParamsProcess,
      checkpreorder::Bool=true)
```

`net`上で`params`を使用して特性をシミュレートします。現時点では、[`ParamsBM`](@ref)（単変量ブラウン運動）および[`ParamsMultiBM`](@ref)（多変量ブラウン運動）型のパラメータのみが受け入れられます。

シミュレーションは、ネットワークのルートから先端までの再帰を使用するため、ノードの前順序が必要です。`checkpreorder=true`（デフォルト）の場合、ネットワークに対して事前に[`PhyloNetworks.preorder!`](@extref)が呼び出されます。そうでない場合は、前順序がすでに計算されていると見なされます。

特性の期待値とシミュレートされた特性値をすべてのノードで持つ[`TraitSimulation`](@ref)型のオブジェクトを返します。

期待値とシミュレートされた特性値にアクセスする例を以下に示します。

# 例

## 単変量

```jldoctest randdoc
julia> phy = readnewick("(A:2.5,((U:1,#H1:0.5::0.4):1,(C:1,(D:0.5)#H1:0.5::0.6):1):0.5);");

julia> par = ParamsBM(1, 0.1) # 期待値1、分散0.1のBM。
ParamsBM:
固定ルートを持つBMのパラメータ:
mu: 1.0
Sigma2: 0.1


julia> sim = rand(phy, par) # ネットワークに沿ってシミュレート
TraitSimulation:
4つの先端を持つネットワーク上の特性シミュレーション結果、BMモデルを使用し、パラメータ:
mu: 1.0
Sigma2: 0.1
```

以下に、再現性のために独自の固定乱数生成器を使用して同じシミュレーションを再実行します。

```jldoctest randdoc
julia> # using Pkg; Pkg.add("StableRNGs") # StableRNGsをインストールするために、まだ行っていない場合

julia> using StableRNGs; rng = StableRNG(791); # 再現性のために

julia> sim = rand(rng, phy, par); # 再シミュレート

julia> traits = sim[:tips] # 先端でのシミュレートされた値を抽出。
4-element Vector{Float64}:
 0.5991561486238962
 0.861066346792992
 1.367634062992289
 1.6439310845929571

julia> tiplabels(sim) # 先端の名前、上記の値と同じ順序
4-element Vector{String}:
 "A"
 "U"
 "C"
 "D"
```

例えば、税on U（2番目にリストされている）のシミュレートされた特性値は約0.86です。内部ノードでシミュレートされた値や、すべてのノードで一度にアクセスしたい場合もあります：

```jldoctest randdoc
julia> traits = sim[:internalnodes] # 内部ノードでのシミュレートされた値を抽出。順序: sim.M.internalnodenumbersのように
5-element Vector{Float64}:
 1.0716684901027937
 1.6007823049044083
 1.6756374575490327
 1.2194286026283034
 1.0

julia> traits = sim[:all] # すべてのノードでのシミュレートされた値、sim.M.nodenumbers_toporderのように順序付け
9-element Vector{Float64}:
 1.0
 1.2194286026283034
 1.6756374575490327
 1.367634062992289
 1.0716684901027937
 1.6007823049044083
 1.6439310845929571
 0.861066346792992
 0.5991561486238962
```

期待値（ノイズなし）を抽出したい場合もあります。これは標準BMモデルではあまり興味深くありませんが、より複雑なモデル（例えば、シフトを伴うモデル）では興味深くなるかもしれません。追加の`:exp`インデックスを使用してこれを行うことができます：

```jldoctest randdoc
julia> traits = sim[:tips, :exp] # 先端での期待値（sim[:all, :exp]およびsim[:internalnodes, :exp]にも有効）。
4-element Vector{Float64}:
 1.0
 1.0
 1.0
 1.0
```

## 多変量

```jldoctest randdoc
julia> phy = readnewick("(A:2.5,((B:1,#H1:0.5::0.4):1,(C:1,(V:0.5)#H1:0.5::0.6):1):0.5);");

julia> par = ParamsMultiBM([1.0, 2.0], [1.0 0.5; 0.5 1.0]) # 期待値[1.0, 2.0]、分散[1.0 0.5; 0.5 1.0]のBM。
ParamsMultiBM:
固定ルートを持つMBDのパラメータ:
mu: [1.0, 2.0]
Sigma: [1.0 0.5; 0.5 1.0]

julia> using StableRNGs; rng = StableRNG(9851); # 再現性のために

julia> sim = rand(rng, phy, par) # 系統樹上でシミュレート
TraitSimulation:
4つの先端を持つネットワーク上の特性シミュレーション結果、MBDモデルを使用し、パラメータ:
mu: [1.0, 2.0]
Sigma: [1.0 0.5; 0.5 1.0]


julia> traits = sim[:tips] # 先端でのシミュレートされた値を抽出（各列は1つのノードのシミュレートされた特性を含む）。
2×4 Matrix{Float64}:
 3.8013    0.839485  0.346092  1.91131
 5.91725  -0.59143   0.458569  0.629048
```

2行は2つの相関特性に対応し、列は4つの税on（先端）に対応します。税onがリストされる順序は`tiplabels`で取得されます：

```jldoctest randdoc
julia> tiplabels(sim)
4-element Vector{String}:
 "A"
 "B"
 "C"
 "V"
```

単変量の場合と同様に、内部ノードでシミュレートされた値や、すべてのノード（ただし前順序でリストされる）や期待値を抽出することもできます。

```jldoctest randdoc
julia> sim[:internalnodes] # 内部ノードでのシミュレートされた値。順序: sim.M.internalnodenumbersと同じ
2×5 Matrix{Float64}:
 -0.604224  0.755722  2.14755  0.484292  1.0
 -0.338922  0.373921  1.15174  0.695561  2.0

julia> traits = sim[:all]; # 2×9 Matrix: すべてのノードでの値、sim.M.nodenumbers_toporderのように順序付け

julia> sim[:tips, :exp] # 期待値（sim[:all, :exp]およびsim[:internalnodes, :exp]にも有効）
2×4 Matrix{Float64}:
 1.0  1.0  1.0  1.0
 2.0  2.0  2.0  2.0
```
