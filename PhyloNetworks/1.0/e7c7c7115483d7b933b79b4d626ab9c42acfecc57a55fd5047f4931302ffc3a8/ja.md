```
readmultinewick(filename::AbstractString, fast=true)
readmultinewick(newicktrees_list::Vector{<:AbstractString})
```

親括弧形式のネットワークのリストを読み込みます。入力がファイルへのパスを示す文字列の場合はファイルから（1行に1つのネットワーク）、または各文字列がnewick形式のトポロジーに対応する文字列のベクターから読み込みます。デフォルトでは（`fast=true`）、`Functors.fmap`が使用され、newickツリーをHybridNetwork型オブジェクトに繰り返し読み込みます。オプション`fast=false`はv0.14.3までの動作に対応しており、ファイル名を入力として与えた場合、系統樹が解析できないときにメッセージを表示し（失敗せず）、空行を許可します。各ネットワークは[`readnewick`](@ref)で読み込まれます。

HybridNetworkオブジェクトの配列を返します。

# 例

```julia
julia> multitreepath = joinpath(dirname(Base.find_package("PhyloNetworks")), "..", "examples", "multitrees.newick");
julia> multitree = readmultinewick(multitreepath) # 25のHybridNetworksのベクター
julia> multitree = readmultinewick(multitreepath, false) # 同じだが遅くて安全
julia> treestrings = readlines(multitreepath) # 25の文字列のベクター
julia> multitree = readmultinewick(treestrings)
julia> readmultinewick(treestrings, false) # 同じだが遅い
```
