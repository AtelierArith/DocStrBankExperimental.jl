```julia
vertex(
    ng::NestedGraphs.NestedGraph,
    cv::Tuple{T, T} where T<:Integer
) -> Union{Nothing, Int64}

```

ローカルビュー `NestedVertex` をグローバルビューに変換します。
