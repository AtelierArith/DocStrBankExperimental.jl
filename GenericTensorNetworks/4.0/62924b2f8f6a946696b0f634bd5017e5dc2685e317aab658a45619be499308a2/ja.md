```
ConfigSampler{N,S,C} <: AbstractSetNumber
ConfigSampler(elements::StaticElementVector)
```

1つの構成をサンプリングするための代数で、`N`は構成の長さ、`C`は`UInt64`の単位でのストレージのサイズ、`S`は構成内の単一要素を格納するためのビット幅、すなわち`log2(# of flavors)`であり、ビット列の場合は`1`です。

!!! note
    `ConfigSampler`は**確率的**な可換半環であり、2つの構成サンプラーを加算しても決定論的な結果は得られません。


## フィールド

  * `data`はサンプリングされた解としての[`StaticElementVector`](@ref)です。

## 例

```jldoctest; setup=:(using GenericTensorNetworks, Random; Random.seed!(2))
julia> ConfigSampler(StaticBitVector([1,1,1,0,0]))
ConfigSampler{5, 1, 1}(11100)

julia> ConfigSampler(StaticBitVector([1,1,1,0,0])) + ConfigSampler(StaticBitVector([1,0,1,0,0]))
ConfigSampler{5, 1, 1}(10100)

julia> ConfigSampler(StaticBitVector([1,1,1,0,0])) * ConfigSampler(StaticBitVector([0,0,0,0,1]))
ConfigSampler{5, 1, 1}(11101)

julia> one(ConfigSampler{5, 1, 1})
ConfigSampler{5, 1, 1}(00000)

julia> zero(ConfigSampler{5, 1, 1})
ConfigSampler{5, 1, 1}(11111)
```
