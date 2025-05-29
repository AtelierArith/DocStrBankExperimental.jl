```
getfields(obj) -> NamedTuple
getfields(obj::Tuple) -> Tuple
```

`obj`のフィールドを含む`NamedTuple`を返します。`Tuple`の場合、`getfields`は恒等関数となります。なぜなら、`Tuple`のフィールドには象徴的な名前がないからです。

# 例

```jldoctest
julia> using ConstructionBase

julia> struct S{A,B}
           a::A
           b::B
       end

julia> getfields(S(1,2))
(a = 1, b = 2)

julia> getfields((a=10,b=20))
(a = 10, b = 20)

julia> getfields((4,5,6))
(4, 5, 6)
```

# 仕様

`getfields`は[生のレベル](@ref the-raw-level)に属します。意味的には`getfields`は`getfield`と`fieldnames`に帰着します：

```julia
function getfields(obj::T) where {T}
    fnames = fieldnames(T)
    NamedTuple{fnames}(getfield.(Ref(obj), fnames))
end
```

しかし、実際の実装はより最適化される可能性があります。組み込み型に対しては、この意味からの逸脱もあります：

  * `getfields(::Tuple)::Tuple`は、`Tuple`には象徴的なフィールド名がないためです。
  * `Base`には`undef`フィールドを持つ型がいくつかあります。これにアクセスするとエラーが発生するため、`getfields`はこれらを省略します。

# 実装

ユーザー定義型に対して`getfields`の意味は変更されるべきではありません。構造体の順序で生のフィールドを`NamedTuple`として返すべきです。言い換えれば、次のように等価であるべきです。

```julia
function getfields(obj::T) where {T}
    fnames = fieldnames(T)
    NamedTuple{fnames}(getfield.(Ref(obj), fnames))
end
```

たとえそれが`obj`のプライベートフィールドを含んでいてもです。意味の変更が望ましい場合は、代わりに[`getproperties`](@ref)をオーバーロードすることを検討してください。[`getproperties`](@ref)、[`constructorof`](@ref)も参照してください。
