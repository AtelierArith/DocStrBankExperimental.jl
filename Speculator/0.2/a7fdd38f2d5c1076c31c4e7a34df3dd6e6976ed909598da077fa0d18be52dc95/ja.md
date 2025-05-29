```
冗長性
```

[`speculate`](@ref)中に表示されるログステートメントを決定するフラグです。

これはセットとしてモデル化されており、[`silent`](@ref)は空のセットです。非空のコンポーネントフラグは[`debug`](@ref)、[`review`](@ref)、および[`warn`](@ref)です。

# インターフェース

この型は`AbstractSet`インターフェースの一部を実装しています。

  * `intersect(::Verbosity, ::Verbosity...)`
  * `isdisjoint(::Verbosity, ::Verbosity)`
  * `isempty(::Verbosity)`
  * `issetequal(::Verbosity, ::Verbosity)`
  * `issubset(::Verbosity, ::Verbosity)`
  * `setdiff(::Verbosity, ::Verboosity...)`
  * `show(::IO, ::Verbosity)`
  * `symdiff(::Verbosity, ::Verbosity...)`
  * `union(::Verbosity, ::Verbosity...)`

# 例

```jldoctest
julia> silent
silent::Verbosity

julia> debug ∪ review
(debug ∪ review)::Verbosity

julia> debug ⊆ debug ∪ review
true

julia> debug ⊆ warn
false
```
