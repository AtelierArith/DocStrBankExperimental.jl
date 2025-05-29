```
mutual_information!(
    mi::MutualInformationContainer,
    fixed,
    buffer,
    full_image,
    moving_bbox,
    range_x,
    range_y,
    ::Missing;
    set_buffer!,
    get_buffer_crop,
    prefilter_frame_crop! = x -> nothing,
)
```

`range_x` と `range_y` のすべてのシフトにおける2つの画像の相互情報を計算します。`fixed` 画像はすでにフィルタリングされている必要があります。これにより `buffer` が設定され、その内容が `prefilter_frame_crop!` を使用してフィルタリングされます。
