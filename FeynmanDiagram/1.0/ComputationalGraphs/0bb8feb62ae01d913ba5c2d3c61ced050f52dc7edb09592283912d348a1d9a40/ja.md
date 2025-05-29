```
function feynman_diagram(subgraphs::Vector{FeynmanGraph{F,W}}, topology::Vector{Vector{Int}}, perm_noleg::Union{Vector{Int},Nothing}=nothing;
    factor=one(_dtype.factor), weight=zero(_dtype.weight), name="", diagtype::DiagramType=GenericDiag()) where {F,W}
```

すべてのサブグラフとトポロジー（頂点間の接続）からフェインマン図を表すFeynmanGraphを作成します。各ExternalVertexは`vertices`で与えられ、内部頂点は`vertices`内のグラフの外部脚を使用して構築されるか、単に`vertices`内のOperatorProductになります。

# 引数:

  * `subgraphs::Vector{FeynmanGraph{F,W}}` 図のすべてのサブグラフ。サブグラフのすべての外部演算子は新しい図のすべての演算子を構成します。
  * `topology::Vector{Vector{Int}}` 図のトポロジー。各`Vector{Int}`は、互いに接続された演算子のインデックスを格納します（伝播子として）。
  * `perm_noleg::Union{Vector{Int},Nothing}=nothing` すべての非脚外部演算子の順列。デフォルトでは、何も設定しないとサブグラフからのデフォルトの順序が使用されます。
  * `factor::F` この図の全体的なスカラー乗法因子（例：順列符号）
  * `weight` 図の重み
  * `name` 図の名前
  * `diagtype` 図のタイプ

# 例:

```julia-repl
julia> V = [𝑓⁺(1)𝑓⁻(2)𝜙(3), 𝑓⁺(4)𝑓⁻(5)𝜙(6), 𝑓⁺(7)𝑓⁻(8)𝜙(9)];
julia> g = feynman_diagram(interaction.(V), [[1, 5], [3, 9], [4, 8]], [3, 1, 2])
7:f⁺(1)f⁻(2)ϕ(3)|f⁺(4)f⁻(5)ϕ(6)|f⁺(7)f⁻(8)ϕ(9)=0.0=Ⓧ (1,2,3,4,5,6)

julia> g.subgraphs
6-element Vector{FeynmanGraph{Float64, Float64}}:
 1:f⁺(1)f⁻(2)ϕ(3)=0.0
 2:f⁺(4)f⁻(5)ϕ(6)=0.0
 3:f⁺(7)f⁻(8)ϕ(9)=0.0
 4:f⁺(1)|f⁻(5)⋅-1.0=0.0
 5:ϕ(3)|ϕ(9)=0.0
 6:f⁺(4)|f⁻(8)⋅-1.0=0.0
```
