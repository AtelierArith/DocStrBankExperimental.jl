```
unpack(table, f1, f2, ... fk;
       wrap_singles=false,
       shuffle=false,
       rng::Union{AbstractRNG,Int,Nothing}=nothing,
       coerce_options...)
```

任意のTables.jl互換の`table`を、述語`f1`、`f2`、...、`fk`によって決定される列の選択によって、小さなテーブルまたはベクトルに水平方向に分割します。列名からの選択は置換なしで行われます。*述語*は、`f(name)`が`table`の各列`name::Symbol`に対して`true`または`false`となる任意のオブジェクト`f`です。

指定された述語の数よりも1つ長いテーブル/ベクトルのタプルを返し、最後のコンポーネントには以前に選択されなかったすべての列が含まれます。

```julia-repl
julia> table = DataFrame(x=[1,2], y=['a', 'b'], z=[10.0, 20.0], w=["A", "B"])
2×4 DataFrame
 Row │ x      y     z        w
     │ Int64  Char  Float64  String
─────┼──────────────────────────────
   1 │     1  a        10.0  A
   2 │     2  b        20.0  B

julia> Z, XY, W = unpack(table, ==(:z), !=(:w));
julia> Z
2-element Vector{Float64}:
 10.0
 20.0

julia> XY
2×2 DataFrame
 Row │ x      y
     │ Int64  Char
─────┼─────────────
   1 │     1  a
   2 │     2  b

julia> W  # 残された列
2-element Vector{String}:
 "A"
 "B"
```

返されたテーブルが単一の列を含む場合、それは`wrap_singles=true`でない限りベクトルに変換されます。

`coerce_options`が指定されている場合、最初に`table`は`coerce(table, coerce_options)`で置き換えられます。詳細については[`ScientificTypes.coerce`](@ref)を参照してください。

`shuffle=true`の場合、`rng`が指定されていない限り、グローバルRNGを使用して最初に`table`の行がシャッフルされます。`rng`が整数の場合、自動生成されたメルセンヌツイスタのシードを指定します。`rng`が指定されている場合、`shuffle=true`は暗黙的です。
