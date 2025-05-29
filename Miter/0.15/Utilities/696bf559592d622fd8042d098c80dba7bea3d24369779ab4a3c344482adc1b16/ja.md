```julia
balanced_matrix(
    vector_or_itr;
    width_bias,
    row_major,
    width,
    height
)

```

ベクトル（または反復可能なもの）の要素を `(height, width)` 行列に配置し、`width / height ≈ width_bias` となるようにします。余分な要素は `nothing` で埋められます。

`row_major = true`（デフォルト）の場合、要素は行優先で配置されます。

この関数の目的は、[`Tableau`](@ref) のようなバランスの取れた表示を作成することです。

`width` と `height` は明示的に指定することもでき、その場合 `width_bias` は使用されません。
