```
reconstruct(obj, data, [flattentrait::Function], [use::Type], [ignore::Type])
```

既存のオブジェクトとタプルまたはベクターデータからオブジェクトを再構築します。データは、objのクエリされたフィールドと同じ長さ以上である必要があります。クエリタイプとフラッテントレイト引数はオプションですが、`ignore`を渡すには`use`を渡す必要があります。

# 引数

  * `obj`: 再構築されるターゲットタイプ
  * `data`: 置き換えデータ - `AbstractArray`、`Tuple`、または`getfield`を定義するタイプ。
  * `flattentrait`: Boolを返す関数で、FielMetadataメソッドのようなもの。形式は次の通りです: `f(::Type, ::Type{Val{:fieldname}}) = true`
  * `use`: タプルで返すタイプまたはタイプの`Union`。
  * `ignore`: 完全に無視するタイプまたはタイプの`Union`。これらは返されず、再帰的に処理されません。

# 例

```julia
julia> struct Foo{A,B,C}
           a::A
           b::B
           c::C
       end

julia> reconstruct(Foo(1, 2, 3), (1, :two, 3.0))
Foo{Int64,Symbol,Float64}(1, :two, 3.0)
```
