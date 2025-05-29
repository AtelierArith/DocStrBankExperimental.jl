```julia
fullfactorial(
    factors::Tuple
) -> Base.Iterators.ProductIterator

```

カテゴリカル因子レベルを表す配列のタプルを受け取り、`Base.Iterators.ProductIterator`を返します。これにより、フルファクタリアルデザインは任意の大きさにすることができ、必要に応じてのみ計算されます。明示的なフルファクタリアルデザインを計算するには、[`explicit_fullfactorial`](@ref)を使用してください。

```jldoctest
julia> fullfactorial(Tuple([-1, 1] for i = 1:10))
Base.Iterators.ProductIterator{NTuple{10, Vector{Int64}}}(([-1, 1], [-1, 1], [-1, 1], [-1, 1], [-1, 1], [-1, 1], [-1, 1], [-1, 1], [-1, 1], [-1, 1]))

```
