```
LensAssembly{T<:Real}
```

光学システムの要素を含む構造体で、これらは [`CSGTree`](@ref) または [`Surface`](@ref) オブジェクトです。

型の曖昧さを防ぐために、各要素数に対して特注の構造体が作成されます。例えば `LensAssembly3` のように、曖昧さを防ぐために要素の型によってパラメータ化されています。[`Rectangle`](@ref) のような基本的な表面型（大量に発生する可能性がある）は `Vector` に独立して格納されるため、CSGオブジェクトには型パラメータが必要です。

各構造体は次のようになります：

```julia
struct LensAssemblyN{T,T1,T2,...,TN} <: LensAssembly{T}
    axis::SVector{3,T}
    rectangles::Vector{Rectangle{T}}
    ellipses::Vector{Ellipse{T}}
    hexagons::Vector{Hexagon{T}}
    paraxials::Vector{ParaxialLens{T}}
    E1::T1
    E2::T2
    ...
    EN::TN
end
```

ここで `Ti <: Union{Surface{T},CSGTree{T}}` です。

LensAssemblyオブジェクトを作成するには、次の関数を使用できます：

```julia
LensAssembly(elements::Vararg{Union{Surface{T},CSGTree{T},LensAssembly{T}}}; axis = SVector(0.0, 0.0, 1.0)) where {T<:Real}
```
