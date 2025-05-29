```
DirectedHypergraph{T} <: AbstractDirectedHypergraph{Tuple{Union{T, Nothing}, Union{T, Nothing}}}
```

A directed hypergraph storing information about vertices and hyperedges.

This implementation is based on guidance from Przemysław Szufel;     see https://github.com/pszufe/SimpleHypergraphs.jl/issues/45 This allows us to manipulate DirectedHypergraphs using Hypergraph functionality There is danger of a user manipulating individual `hg_tail` and `hg_head` (undirected) hypergraphs Is there a smart way to prevent this? TODO: reconsider this design choice

**Constructors**

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

Construct a hypergraph with a given number of vertices and hyperedges. Optionally, values of type `V` can be stored at vertices and values of type `E` can be stored at hyperedges. By default the hypergraph uses a `Dict{Int,T}` for the internal data storage, however a different dictionary such as `SortedDict` to ensure result replicability can be used (e.g. when doing stochastic simulations on hypergraphs).

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

Construct a directed hypergraph using its matrix representation. In the matrix representation rows are vertices and columns are hyperedges. Optionally, values of type `V` can be stored at vertices and values of type `E` can be stored at hyperedges. By default the hypergraph uses a `Dict{Int,T}` for the internal data storage, however a different dictionary such as `SortedDict` to ensure result replicability can be used (e.g. when doing stochastic simulations on hypergraphs).

```
DirectedHypergraph(g::Graphs.DiGraph)
```

Constructs a directed hypergraph of degree 2 by making a deep copy of a Graphs.DiGraph. A `SortedDict` will be used for internal data storage of the hypergraph.

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

Constructs a directed hypergraph from two undirected basic hypergraphs, one with hyperedges containing "tail" vertices and one with hyperedges containing "head" verticies.

```
DirectedHypergraph{T,V,E,D}(
    hg_tail::Hypergraph{T,V,E,D},
    hg_head::Hypergraph{T,V,E,D}
) where {T<:Real,V,E,D<:AbstractDict{Int, T}}
```

Constructs a directed hypergraph from two hypergraphs potentially containing metadata. Throws an error if the vertex metadata of the two hypergraphs is not element-for-element identical.

**Arguments**

  * `T` : type of weight values stored in the hypergraph's adjacency matrix
  * `V` : type of values stored in the vertices of the hypergraph
  * `E` : type of values stored in the edges of the hypergraph
  * `D` : dictionary for storing values the default is `Dict{Int, T}`
  * `n` : number of vertices
  * `k` : number of hyperedges
  * `m` : a matrix representation rows are vertices and columns are hyperedges
  * `g` : a (directed) graph representation of the hypergraph
  * `hg_tail`: an undirected hypergraph representing the tail half of   the directed hypergraph
  * `hg_head`: an undirected hypergraph representing the head half of   the directed hypergraph
