```
factor(ContainerType, n::Integer) -> ContainerType
```

`n`の因数分解を`ContainerType`に格納して返します。`ContainerType`は`AbstractDict`または`AbstractArray`のサブタイプ、`Set`、または`BitSet`でなければなりません。

```julia
julia> factor(DataStructures.SortedDict, 100)
DataStructures.SortedDict{Int64,Int64,Base.Order.ForwardOrdering} with 2 entries:
  2 => 2
  5 => 2
```

`ContainerType <: AbstractArray`の場合、これは`n`のすべての素因数を重複を含めて、ソートされた順序で返します。

```julia
julia> factor(Vector, 100)
4-element Array{Int64,1}:
 2
 2
 5
 5

julia> prod(factor(Vector, 100)) == 100
true
```

`ContainerType == Set`の場合、これは異なる素因数をセットとして返します。

```julia
julia> factor(Set, 100)
Set([2,5])
```
