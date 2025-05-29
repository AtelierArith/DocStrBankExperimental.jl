```
DirectedHypergraph{T} <: AbstractDirectedHypergraph{Tuple{Union{T, Nothing}, Union{T, Nothing}}}
```

頂点とハイパエッジに関する情報を格納する有向ハイパグラフです。

この実装はPrzemysław Szufelからの指導に基づいています; https://github.com/pszufe/SimpleHypergraphs.jl/issues/45 これにより、ハイパグラフ機能を使用して有向ハイパグラフを操作できます。ユーザーが個々の `hg_tail` および `hg_head`（無向）ハイパグラフを操作する危険があります。これを防ぐためのスマートな方法はありますか？TODO: この設計選択を再考する

**コンストラクタ**

```
DirectedHypergraph{T}(n::Integer,k::Integer) where {T<:Real}
DirectedHypergraph{T,V}(n::Integer, k::Integer;
    v_meta=Vector{Union{V,Nothing}}(nothing, n)
    ) where {T<:Real, V}
DirectedHypergraph{T,E}(n::Integer, k::Integer;
    he_meta_tail=Vector{Union{E,Nothing}}(nothing, k),
    he_meta_head=Vector{Union{E,Nothing}}(nothing, k)
    ) where {T<:Real, E}
DirectedHypergraph{T,V,E}(n::Integer, k::Integer;
    v_meta=Vector{Union{V,Nothing}}(nothing, n),
    he_meta_tail=Vector{Union{E,Nothing}}(nothing, k),
    he_meta_head=Vector{Union{E,Nothing}}(nothing, k)
    ) where {T<:Real, V, E}
DirectedHypergraph{T,V,E,D}(n::Integer, k::Integer,
    v_meta=Vector{Union{V,Nothing}}(nothing, n),
    he_meta_tail=Vector{Union{E,Nothing}}(nothing, k),
    he_meta_head=Vector{Union{E,Nothing}}(nothing, k)
    ) where {T<:Real,V,E,D<:AbstractDict{Int,T}}
```

指定された数の頂点とハイパエッジを持つハイパグラフを構築します。オプションで、型 `V` の値を頂点に格納し、型 `E` の値をハイパエッジに格納できます。デフォルトでは、ハイパグラフは内部データストレージに `Dict{Int,T}` を使用しますが、結果の再現性を確保するために `SortedDict` などの別の辞書を使用することもできます（例：ハイパグラフ上で確率的シミュレーションを行うとき）。

```
DirectedHypergraph(
    m_tail::AbstractMatrix{Union{T, Nothing}},
    m_head::AbstractMatrix{Union{T, Nothing}}
) where {T<:Real}    
DirectedHypergraph{T}(
    m_tail::AbstractMatrix{Union{T, Nothing}},
    m_head::AbstractMatrix{Union{T, Nothing}}
) where {T<:Real}
DirectedHypergraph{T,V}(
    m_tail::AbstractMatrix{Union{T, Nothing}},
    m_head::AbstractMatrix{Union{T, Nothing}};
    v_meta::Vector{Union{Nothing,V}}=Vector{Union{Nothing,V}}(nothing, size(m,1)),
) where {T<:Real,V}
DirectedHypergraph{T,E}(
    m_tail::AbstractMatrix{Union{T, Nothing}},
    m_head::AbstractMatrix{Union{T, Nothing}};
    he_meta_tail::Vector{Union{Nothing,E}}=Vector{Union{Nothing,E}}(nothing, size(m,2)),
    he_meta_head::Vector{Union{Nothing,E}}=Vector{Union{Nothing,E}}(nothing, size(m,2))
) where {T<:Real,E}
DirectedHypergraph{T,V,E}(
    m_tail::AbstractMatrix{Union{T, Nothing}},
    m_head::AbstractMatrix{Union{T, Nothing}};
    v_meta::Vector{Union{Nothing,V}}=Vector{Union{Nothing,V}}(nothing, size(m,1)),
    he_meta_tail::Vector{Union{Nothing,E}}=Vector{Union{Nothing,E}}(nothing, size(m,2)),
    he_meta_head::Vector{Union{Nothing,E}}=Vector{Union{Nothing,E}}(nothing, size(m,2))
) where {T<:Real,V,E}
DirectedHypergraph{T,V,E,D}(
    m_tail::AbstractMatrix{Union{T, Nothing}},
    m_head::AbstractMatrix{Union{T, Nothing}};
    v_meta::Vector{Union{Nothing,V}}=Vector{Union{Nothing,V}}(nothing, size(m,1)),
    he_meta_tail::Vector{Union{Nothing,E}}=Vector{Union{Nothing,E}}(nothing, size(m,2)),
    he_meta_head::Vector{Union{Nothing,E}}=Vector{Union{Nothing,E}}(nothing, size(m,2))
) where {T<:Real,V,E,D<:AbstractDict{Int,T}}
```

行が頂点、列がハイパエッジである行列表現を使用して有向ハイパグラフを構築します。オプションで、型 `V` の値を頂点に格納し、型 `E` の値をハイパエッジに格納できます。デフォルトでは、ハイパグラフは内部データストレージに `Dict{Int,T}` を使用しますが、結果の再現性を確保するために `SortedDict` などの別の辞書を使用することもできます（例：ハイパグラフ上で確率的シミュレーションを行うとき）。

```
DirectedHypergraph(g::Graphs.DiGraph)
```

Graphs.DiGraphの深いコピーを作成することで、次数2の有向ハイパグラフを構築します。ハイパグラフの内部データストレージには `SortedDict` が使用されます。

```
DirectedHypergraph{T,V,D}(
    hg_tail::Hypergraph{T,D},
    hg_head::Hypergraph{T,D};
    v_meta::Vector{Union{Nothing,V}}=Vector{Union{Nothing,V}}(nothing, size(m,1)),
) where {T<:Real,V,D<:AbstractDict{Int, T}}
DirectedHypergraph{T,E,D}(
    hg_tail::Hypergraph{T,D},
    hg_head::Hypergraph{T,D};
    he_meta_tail::Vector{Union{Nothing,E}}=Vector{Union{Nothing,E}}(nothing, size(m,2)),
    he_meta_head::Vector{Union{Nothing,E}}=Vector{Union{Nothing,E}}(nothing, size(m,2))
) where {T<:Real,E,D<:AbstractDict{Int, T}}
DirectedHypergraph{T,V,E,D}(
    hg_tail::Hypergraph{T,D},
    hg_head::Hypergraph{T,D};
    v_meta::Vector{Union{Nothing,V}}=Vector{Union{Nothing,V}}(nothing, size(m,1)),
    he_meta_tail::Vector{Union{Nothing,E}}=Vector{Union{Nothing,E}}(nothing, size(m,2)),
    he_meta_head::Vector{Union{Nothing,E}}=Vector{Union{Nothing,E}}(nothing, size(m,2))
) where {T<:Real,V,E,D<:AbstractDict{Int, T}}
```

「テール」頂点を含むハイパエッジを持つ1つの無向基本ハイパグラフと、「ヘッド」頂点を含むハイパエッジを持つ1つの無向基本ハイパグラフから有向ハイパグラフを構築します。

```
DirectedHypergraph{T,V,E,D}(
    hg_tail::Hypergraph{T,V,E,D},
    hg_head::Hypergraph{T,V,E,D}
) where {T<:Real,V,E,D<:AbstractDict{Int, T}}
```

メタデータを含む可能性のある2つのハイパグラフから有向ハイパグラフを構築します。2つのハイパグラフの頂点メタデータが要素ごとに同一でない場合、エラーが発生します。

**引数**

  * `T` : ハイパグラフの隣接行列に格納される重み値の型
  * `V` : ハイパグラフの頂点に格納される値の型
  * `E` : ハイパグラフのエッジに格納される値の型
  * `D` : 値を格納するための辞書、デフォルトは `Dict{Int, T}`
  * `n` : 頂点の数
  * `k` : ハイパエッジの数
  * `m` : 行列表現、行は頂点、列はハイパエッジ
  * `g` : ハイパグラフの（有向）グラフ表現
  * `hg_tail`: 有向ハイパグラフのテール部分を表す無向ハイパグラフ
  * `hg_head`: 有向ハイパグラフのヘッド部分を表す無向ハイパグラフ

```
