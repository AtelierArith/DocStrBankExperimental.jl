```
matrices_set(
    daf::DafReader,
    rows_axis::AbstractString,
    columns_axis::AbstractString;
    [relayout::Bool = true]
)::AbstractSet{<:AbstractString}
```

`daf`における`rows_axis`と`columns_axis`の行列プロパティの名前。

`relayout`（デフォルト）の場合、これは他のレイアウトに存在する行列の名前を含む（つまり、軸が反転したもの）。

最初に`rows_axis`と`columns_axis`が`daf`に存在することを確認します。

!!! note
    Juliaには返すための不変集合型がありません。結果の集合を変更すると、悪いことが*起こる*でしょう。

