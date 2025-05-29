```
register!(
    mi::MutualInformationContainer,
    full_image::AbstractArray{T,2},
    fixed::AbstractArray{T,2},
    moving_bbox::AbstractVector{Int},
    max_shift_x::Int,
    max_shift_y::Int,
    buffer::AbstractArray{T,2};
    set_buffer! = (buffer, current_frame, moving_bbox) -> set_buffer!(buffer, current_frame, moving_bbox, max_shift_x, max_shift_y),
    get_buffer_crop = (buffer, moving_bbox, shift_x, shift_y) -> get_buffer_crop(buffer, moving_bbox, shift_x, shift_y, max_shift_x, max_shift_y),
    prefilter_frame_crop! = x -> nothing,
    start_shift_x = 3,
    start_shift_y = 3,
    expand_border = 1,
    expand_increment = 1,
) where {T<:Integer}
```

`moving_bbox`を`fixed`画像に最もよく合わせるシフトを計算します。高レベルでは、これは`full_image`内の`moving_bbox`のビューを`fixed`画像に最もよく一致させることを試みます。これはx軸とy軸に沿ったシフトのみを考慮し、回転は考慮されません。この関数は、できるだけ少ないシフトを評価するために、最大シフトの範囲を段階的に拡張します。最小限、すべてのシフトは`± start_shift_x`および`± start_shift_y`の範囲内で考慮されます。最適なシフトが範囲の`expand_border`内にある場合、範囲は`expand_increment`によって拡張され、すべての新しいシフトが評価されます。このプロセスは、最適なシフトが範囲の`expand_border`内にない場合、または範囲が`max_shift_x`および`max_shift_y`に達するまで繰り返されます。

`moving_bbox`にパディングを追加することは、登録の安定性を向上させるための良いアイデアです。例えば、`my_bbox .+ [-10, -10, 10, 10]`のようにします。データに最適なパディング値を決定する必要があります。

パラメータ`buffer`は、一時的なストレージに必要です。一般的に、`buffer`は`Array{T}(undef, (size(fixed) .+ (MAX_SHIFT * 2))...)`として定義できます。バッファは、各軸の最大および最小のxおよびyシフトによって拡張された`fixed`画像のサイズ以上のサイズを持っている必要があります。パラメータ`set_buffer!`および`get_buffer_crop`は、それぞれこのバッファに書き込み、読み取るために使用されます。通常、これらをデフォルトから変更する必要はありません。

パラメータ`prefilter_frame_crop!`は、2つの画像間の相互情報を計算する前に画像フィルタリングを適用したい場合に指定できます。この関数は、実装したフィルタリング操作で与えられた画像を変更する必要があります。また、`fixed`画像にはフィルタリングが事前に適用されている必要があります。このパッケージのテストを参照して例を確認してください。
