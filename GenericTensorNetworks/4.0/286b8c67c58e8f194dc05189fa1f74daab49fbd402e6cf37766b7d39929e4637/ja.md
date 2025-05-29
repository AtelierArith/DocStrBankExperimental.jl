```
ConfigEnumerator{N,S,C} <: AbstractSetNumber
```

構成を列挙するための集合代数で、`N` は構成の長さ、`C` は `UInt64` の単位でのストレージのサイズ、`S` は構成内の単一要素を格納するためのビット幅、すなわち `log2(# of flavors)` であり、ビット列の場合は `1` です。

## フィールド

  * `data` は解集合としての [`StaticElementVector`](@ref) のベクターです。

## 例

```jldoctest; setup=:(using GenericTensorNetworks)
julia> a = ConfigEnumerator([StaticBitVector([1,1,1,0,0]), StaticBitVector([1,0,0,0,1])])
{11100, 10001}

julia> b = ConfigEnumerator([StaticBitVector([0,0,0,0,0]), StaticBitVector([1,0,1,0,1])])
{00000, 10101}

julia> a + b
{11100, 10001, 00000, 10101}

julia> one(a)
{00000}

julia> zero(a)
{}
```
