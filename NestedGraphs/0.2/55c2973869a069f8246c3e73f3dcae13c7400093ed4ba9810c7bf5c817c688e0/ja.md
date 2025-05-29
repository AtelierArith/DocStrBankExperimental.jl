```julia
roll_vertex(
    ng::NestedGraphs.NestedGraph,
    v::AbstractArray{T<:Integer, 1}
) -> Union{Nothing, Int64}

```

ネストされた内部サブグラフのベクトルを与えると、フラットグラフ内のインデックスを取得します。ベクトルの最後の要素は、`v[1:end-1]` 内部ネストグラフのノード番号として扱われます。
