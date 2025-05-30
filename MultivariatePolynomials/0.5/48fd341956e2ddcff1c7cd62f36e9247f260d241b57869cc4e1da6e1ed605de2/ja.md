```
struct ExponentsIterator{M}(
    object;
    mindegree::Int = 0,
    maxdegree::Union{Nothing,Int} = nothing,
    inline::Bool = false,
)
```

モノミアル順序 `M` のためのモノミアル指数を生成するイテレータです。指数のベクトルの型は `object` の型であり、長さ（すなわち変数の数）は `length(object)` です。

`object` はゼロである必要はなく、`copy` および `setindex!` メソッドを実装している必要があります（特別なケースとして `Tuple` は除きます）。

詳細は [`monomials`](@ref) を参照してください。

### 例

以下の例は、2つの変数のモノミアルのすべての指数を次数2まで生成する方法を示しています。

```jldoctest
julia> collect(ExponentsIterator{Graded{LexOrder}}((0, 0), maxdegree = 2))
6-element Vector{Tuple{Int64, Int64}}:
 (0, 0)
 (0, 1)
 (1, 0)
 (0, 2)
 (1, 1)
 (2, 0)
```

任意の長さの指数のタプルを `ntuple` を使用して簡単に生成できることに注意してください。以下のようにします。

```jldoctest
julia> collect(ExponentsIterator{Graded{LexOrder}}(ntuple(zero, 3), mindegree = 2, maxdegree = 2))
6-element Vector{Tuple{Int64, Int64, Int64}}:
 (0, 0, 2)
 (0, 1, 1)
 (0, 2, 0)
 (1, 0, 1)
 (1, 1, 0)
 (2, 0, 0)
```

モノミアル順序を変更し、`Tuple` の代わりに `Vector` を使用することもできます。以下のようにします。

```jldoctest
julia> collect(ExponentsIterator{LexOrder}(zeros(Int, 2), mindegree = 2, maxdegree = 3))
7-element Vector{Vector{Int64}}:
 [0, 2]
 [0, 3]
 [1, 1]
 [1, 2]
 [2, 0]
 [2, 1]
 [3, 0]
```
