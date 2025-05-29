```
AbstractSingleton{N} <: AbstractHyperrectangle{N}
```

単一の値を持つ集合のための抽象型。

### 注意事項

このインターフェースの標準実装については、[`Singleton`](@ref)を参照してください。

すべての具体的な`AbstractSingleton`は、次の関数を定義する必要があります：

  * `element(::AbstractSingleton)` – 単一の要素を返す

他の関数の中で、次の関数が自動的に定義されます：

  * `element(::AbstractSingleton, i::Int)` – インデックス`i`の単一の要素を返す

```jldoctest; setup = :(using LazySets: subtypes)
julia> subtypes(AbstractSingleton)
2-element Vector{Any}:
 Singleton
 ZeroSet
```
