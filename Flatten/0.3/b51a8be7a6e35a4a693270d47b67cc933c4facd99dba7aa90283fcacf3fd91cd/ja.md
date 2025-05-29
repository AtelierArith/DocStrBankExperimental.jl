```
flatten(obj, [flattentrait::Function], [use::Type], [ignore::Type])
```

フラット化。ネストされた構造体またはタプルをフラットなタプルにフラット化します。クエリタイプとフラットトレイト引数はオプションですが、`ignore`を渡すには`use`を渡す必要があります。

# 引数

  * `obj`: 再構築されるターゲットタイプ
  * `flattentrait`: Boolを返す関数、例えばFielMetadataメソッド。形式は次の通りです: `f(::Type, ::Type{Val{:fieldname}}) = true`
  * `use`: タプルに返すタイプまたはタイプの`Union`。
  * `ignore`: 完全に無視するタイプまたはタイプの`Union`。これらは返されず、再帰的に処理されません。

# 例

```jldoctest
julia> using Flatten

julia> struct Foo{A,B,C}
           a::A
           b::B
           c::C
       end

julia> foo = Foo(1, 2, 3)
Foo{Int64,Int64,Int64}(1, 2, 3)

julia> flatten(foo)
(1, 2, 3)

julia> nested = Foo(Foo(1, 2, 3), 4.0, 5.0)
Foo{Foo{Int64,Int64,Int64},Float64,Float64}(Foo{Int64,Int64,Int64}(1, 2, 3), 4.0, 5.0)

julia> flatten(nested)
(1, 2, 3, 4.0, 5.0)

タプルをベクターに変換するには、単に[flatten(x)...]を使用するか、静的配列を使用してアロケーションを避けます: `SVector(flatten(x))`。
```

フィールドは`flattenable(struct, field)`メソッドを使用してフラット化から除外できます。これらは[FieldMetadata.jl](https://github.com/rafaqz/FieldMetadata.jl)の`@flattenable`を使用して簡単に定義するか、FieldMetadataを使用して独自のカスタム関数を定義するか、手動で次の形式で定義できます:

```julia
julia> import Flatten: flattenable

julia> @flattenable struct Partial{A,B,C}
           a::A | true
           b::B | true
           c::C | false
       end

julia> nestedpartial = Partial(Partial(1.0, 2.0, 3.0), 4, 5)
Partial{Partial{Float64,Float64,Float64},Int64,Int64}(Partial{Float64,Float64,Float64}(1.0, 2.0, 3.0), 4, 5)

julia> nestedpartial = Partial(Partial(1.0, 2.0, 3.0), 4, 5)
Partial{Partial{Float64,Float64,Float64},Int64,Int64}(Partial{Float64,Float64,Float64}(1.0, 2.0, 3.0), 4, 5)

julia> flatten(nestedpartial)
(1.0, 2.0, 4)
```
