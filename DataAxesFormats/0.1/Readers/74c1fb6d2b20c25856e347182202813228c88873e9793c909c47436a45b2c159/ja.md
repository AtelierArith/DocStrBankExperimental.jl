```
axis_vector(
    daf::DafReader,
    axis::AbstractString;
    [default::Union{Nothing, UndefInitializer} = undef]
)::Maybe{AbstractVector{<:AbstractString}}
```

`daf`のいくつかの`axis`のエントリのユニークな名前の配列です。これは、特別な`name`プロパティに対して[`get_vector`](@ref)を実行するのと似ていますが、`NamedVector`の代わりに文字列の単純なベクター（配列）を返します。

`default`が`undef`（デフォルト）の場合、これは`axis`が`daf`に存在することを確認します。それ以外の場合、`default`は`nothing`であり、`axis`が存在しない場合に返されます。
