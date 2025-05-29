```
register!(
    mi::MutualInformationContainer,
    full_image::AbstractArray{T,2},
    fixed::AbstractArray{T,2},
    moving_bbox::AbstractVector{Int},
    range_x::AbstractVector{Int},
    range_y::AbstractVector{Int},
    buffer::AbstractArray{T,2},
    prev_mis::Union{Missing,AbstractArray{Float32,2}};
    set_buffer! = (buffer, current_frame, moving_bbox) -> set_buffer!(buffer, current_frame, moving_bbox, maximum(range_x), maximum(range_y)),
    get_buffer_crop = (buffer, moving_bbox, shift_x, shift_y) -> get_buffer_crop(buffer, moving_bbox, shift_x, shift_y, maximum(range_x), maximum(range_y)),
    prefilter_frame_crop! = x -> nothing,
) where {T<:Integer}
```

`moving_bbox`を`fixed`画像に最もよく合わせるシフトを計算します。高レベルでは、`full_image`内の`moving_bbox`のビューを`fixed`画像に最もよく一致させることを試みます。これはx軸とy軸に沿ったシフトのみを考慮し、回転は考慮されません。`range_x`と`range_y`内のすべてのシフトの組み合わせが考慮されます。

`moving_bbox`にパディングを追加することは、登録の安定性を向上させるための良いアイデアです。例えば、`my_bbox .+ [-10, -10, 10, 10]`のようにします。データに最適なパディング値を決定する必要があります。

パラメータ`buffer`は、この関数への呼び出し間での一時的なストレージに必要です。これは、同様の画像を多く登録するためにこの関数をループで呼び出すことが想定されているためです。一般的に、`buffer`は`Array{T}(undef, (size(fixed) .+ (MAX_SHIFT * 2))...)`として定義できます。バッファは、各軸の最大および最小のxおよびyシフトによって拡張された`fixed`画像のサイズ以上のサイズを持っている必要があります。パラメータ`set_buffer!`と`get_buffer_crop`は、それぞれこのバッファに書き込み、読み取るために使用されます。通常、これらをデフォルトから変更する必要はありません。

パラメータ`prev_mis`は、この関数が「インクリメンタル」に呼び出され、シフトホライズンが拡大している場合に、相互情報量の計算をメモ化するために使用されます。この関数を直接呼び出す場合（最大シフトホライズンを徐々に拡大するためのループ内ではない場合）、これを`missing`に設定する必要があります。これにより、`range_x`と`range_y`内のすべてのシフトの組み合わせが考慮されます。

パラメータ`prefilter_frame_crop!`は、2つの画像間の相互情報量を計算する前に画像フィルタリングを適用したい場合に指定できます。この関数は、実装するフィルタリング操作で与えられた画像を変更する必要があります。また、`fixed`画像にはフィルタリングが事前に適用されている必要があります。このパッケージのテストを参照して、例を確認してください。
