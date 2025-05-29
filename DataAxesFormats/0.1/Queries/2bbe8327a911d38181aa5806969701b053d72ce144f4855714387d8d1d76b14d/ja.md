```
get_frame(
    daf::DafReader,
    axis::QueryString,
    [columns::Maybe{FrameColumns} = nothing;
    cache::Bool = true]
)::DataFrame end
```

複数の同じ `axis` のベクトルを含む `DataFrame` を返します。

`axis` は、単に軸の名前（例: `"cell"`）であるか、軸のクエリ（例: `q"/ cell"`）であるか、マスクを使用することもできます（例: `q"/ cell & age > 1"`）。クエリの結果は、一意の軸エントリ名のベクトルでなければなりません。

`columns` が指定されていない場合、データフレームには軸のすべてのベクトルプロパティがアルファベット順で含まれます（`DataFrame` には名前付き行の概念がないため、最初の列には軸エントリの名前が含まれます）。

デフォルトでは、すべてのクエリの結果がキャッシュされます。これにより、大量のメモリを消費する可能性があります。`cache = false` を指定することで無効にするか、[`empty_cache!`](@ref) を使用してキャッシュデータを解放できます。
