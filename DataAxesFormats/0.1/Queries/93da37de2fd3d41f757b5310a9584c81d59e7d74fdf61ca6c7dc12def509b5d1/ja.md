```
full_vector_query(
    axis_query::Query,
    vector_query::QueryString,
    vector_name::Maybe{AbstractString} = nothing,
)::Query
```

軸に対するクエリと、ベクトルプロパティのサフィックスクエリを組み合わせて、軸のベクトル値に対する完全なクエリを作成します。これは、[`FrameColumn`](@ref) が [`get_frame`](@ref) のために使用し、またビュー内のベクトルデータのクエリにも使用されます。
