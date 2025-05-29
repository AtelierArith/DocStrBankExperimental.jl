```
mutual_information!(
    mi::MutualInformationContainer,
    fixed,
    buffer,
    ::Any,
    moving_bbox,
    range_x,
    range_y,
    prev_mis::AbstractArray{Float32,2};
    get_buffer_crop,
    kwargs...
)
```

2つの画像の相互情報を`range_x`と`range_y`内のすべてのシフトで計算します。以前の結果（`prev_mis`；この関数の以前の呼び出しからの戻り値）を使用して評価をウォームスタートし、`buffer`の以前に設定されたフィルタリングされた内容を使用します。
