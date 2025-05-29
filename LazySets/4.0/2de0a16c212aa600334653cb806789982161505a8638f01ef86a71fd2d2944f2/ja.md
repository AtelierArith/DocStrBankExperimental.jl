```
AbstractHyperrectangle{N} <: AbstractZonotope{N}
```

ハイパーレクタングル集合のための抽象型。

### ノート

このインターフェースの標準実装については、[`Hyperrectangle`](@ref)を参照してください。

すべての具体的な`AbstractHyperrectangle`は、以下の関数を定義する必要があります：

  * `radius_hyperrectangle(::AbstractHyperrectangle)` – ハイパーレクタングルの半径を返します。これは全次元のベクトルです。

他の関数の中で、以下の関数が自動的に定義されます：

  * `isflat(::AbstractHyperrectangle)` – ハイパーレクタングルの半径がある次元でゼロかどうかを確認します。
  * `radius_hyperrectangle(::AbstractHyperrectangle, i::Int)` – `i`-次元におけるハイパーレクタングルの半径を返します。

すべてのハイパーレクタングル集合はゾノトピック集合でもあります。詳細は[`AbstractZonotope`](@ref)を参照してください。

`AbstractHyperrectangle`のサブタイプ（抽象インターフェースを含む）：

```jldoctest; setup = :(using LazySets: subtypes)
julia> subtypes(AbstractHyperrectangle)
5-element Vector{Any}:
 AbstractSingleton
 BallInf
 Hyperrectangle
 Interval
 SymmetricIntervalHull
```
