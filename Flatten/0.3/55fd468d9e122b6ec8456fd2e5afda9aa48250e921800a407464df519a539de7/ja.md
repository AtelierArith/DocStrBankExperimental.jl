```
update!(obj, data, [flattentrait::Function], [use::Type], [ignore::Type])
```

`Tuple` または `Vector` のデータで可変オブジェクトを更新します。クエリタイプとフラットトレイト引数はオプションですが、`ignore` を渡すには `use` を渡す必要があります。

# 引数

  * `obj`: 再構築されるターゲットタイプ
  * `data`: 置き換えデータ - `AbstractArray`、`Tuple` または `getfield` を定義するタイプ。
  * `flattentrait`: Bool を返す関数、例えば FielMetadat メソッド。形式は次の通りです: `f(::Type, ::Type{Val{:fieldname}}) = true`
  * `use`: タプルで返すタイプ。
  * `ignore`: 完全に無視するタイプ。これらは返されず、再帰的にも処理されません。

# 例

```jldoctest
julia> using Flatten

julia> mutable struct MutableFoo{A,B,C}
           a::A
           b::B
           c::C
       end

julia> mufoo = MutableFoo(1, 2, 3)
MutableFoo{Int64,Int64,Int64}(1, 2, 3)

julia> update!(mufoo, (2, 4, 6))
MutableFoo{Int64,Int64,Int64}(2, 4, 6)

julia> mufoo = MutableFoo(1, 2, :three)
MutableFoo{Int64,Int64,Symbol}(1, 2, :three)

julia> update!(mufoo, (:foo,), Symbol)
MutableFoo{Int64,Int64,Symbol}(1, 2, :foo)
```
