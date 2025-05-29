```
warp(img, tform, [indices]; kwargs...) -> imgw
```

`img`の座標を変換し、新しい`imgw`を返します。`imgw[I] = img[tform(I)]`が成り立ちます。

# 出力

出力配列`imgw`は`OffsetArray`です。手動で指定しない限り、一般的には`axes(imgw) == axes(img)`は成り立ちません。単純な配列が欲しい場合は、`parent(imgw)`または`OffsetArrays.no_offset_view(imgw)`を使ってカスタムインデックスを「ストリップ」できます。

# 引数

  * `img`: 座標変換が必要な元の画像。
  * `tform`: 座標変換関数または関数のようなオブジェクトで、[`SVector`](https://github.com/JuliaArrays/StaticArrays.jl)を入力として受け入れる必要があります。さまざまな変換を作成するのに便利なパッケージは[CoordinateTransformations.jl](https://github.com/FugroRoames/CoordinateTransformations.jl)です。
  * `indices`（オプション）: 出力画像の軸を指定します。デフォルトでは、`imgw`は[`autorange`](@ref ImageTransformations.autorange)を使用して`img`のすべての元のピクセルを含むようにインデックスが計算されます。これを行うには`inv(tform)`を計算する必要があります。与えられた変換`tform`が`inv`をサポートしていない場合、`indices`パラメータを手動で指定する必要があります。

# パラメータ

!!! info
    `method`および`fillvalue`の値を構築するには、最初に`Interpolations`パッケージをロードする必要があります。


  * `method::Union{Degree, InterpolationType}`: 使用したい補間方法。デフォルトは`BSpline(Linear())`です。メソッドインスタンスを構築するには、`Interpolations`をロードする必要があります。
  * `fillvalue`: 新しい領域を埋めるために使用される値。デフォルト値は、可能であれば`NaN`、そうでなければ`0`です。外挿境界条件を渡すこともできます: `Flat()`, `Reflect()`および`Periodic()`。

# 参照

`warp`のいくつかの高レベルインターフェースがあります:

  * 画像の回転: [`imrotate`](@ref)
  * 画像のリサイズ: [`imresize`](@ref)

`warp`の遅延バージョンもあります:

  * [`WarpedView`](@ref)は、メモリを割り当てない点を除いて`warp`とほぼ同等です。
  * [`InvWarpedView(img, tform, [indices]; kwargs...)`](@ref ImageTransformations.InvWarpedView)は、`warp(img, inv(tform), [indices]; kwargs...)`とほぼ同等ですが、メモリを割り当てません。

# 拡張ヘルプ

## パラメータの詳細

このアプローチは、バックワードモードのワーピングとして知られています。「バックワード」と呼ばれるのは、内部の座標変換が実際には`axes(imgr)`から`axes(img)`への逆マップだからです。

`AbstractExtrapolation`オブジェクトを構築し、それを`warp`に`img`として渡すことで、補間動作を手動で指定できます。ただし、これは通常面倒です。このため、`warp`中に`AbstractExtrapolation`オブジェクトを便利に構築するための2つのキーワード`method`と`fillvalue`があります。

!!! warning
    `img`が`AbstractExtrapolation`の場合、追加の`method`および`fillvalue`キーワードは無視されます。


### `method::Union{Degree, InterpolationType}`

ラップされた画像の値を再構築するために使用したい補間方法。

可能な`InterpolationType`の選択肢の中には、他の言語で使用したことがあるかもしれない一般的な方法があります:

  * 最近傍: `BSpline(Constant())`
  * 三角形/バイリニア: `BSpline(Linear())`
  * バイキュービック: `BSpline(Cubic(Line(OnGrid())))`
  * ランツォス2: `Lanczos(2)`
  * ランツォス3: `Lanczos(3)`
  * ランツォス4: `Lanczos(4)`または`Lanczos4OpenCV()`

`Degree`を渡す場合、`BSpline`であることが期待されます。例えば、`Linear()`は`BSpline(Linear())`と同等です。

### `fillvalue`

`tform(I)`が元の`img`の外のインデックスにマッピングされる場合、その位置は`fillvalue`の値に設定されます。デフォルトのfillvalueは、`img`の要素型がそれをサポートしている場合は`NaN`、そうでなければ`0`です。

`fillvalue`パラメータは、`Number`または`Colorant`のいずれかであることができます。この場合、最初に`eltype(imgr)`に変換されます。例えば、`fillvalue = 1`は`Gray(1)`に変換され、外部インデックスを白いピクセルで埋めます。

また、`fillvalue`は外挿スキームであることもできます: `Flat()`, `Periodic()`および`Reflect()`。これらのスキームを理解する最良の方法は、小さな例で試してみることです:

```jldoctest
julia> using ImageTransformations, TestImages, Interpolations

julia> using OffsetArrays: IdOffsetRange

julia> img = testimage("lighthouse");

julia> imgr = imrotate(img, π/4; fillvalue=Flat()); # ゼロ外挿傾斜

julia> imgr = imrotate(img, π/4; fillvalue=Periodic()); # 周期的境界

julia> imgr = imrotate(img, π/4; fillvalue=Reflect()); # ミラー境界

julia> axes(imgr)
(IdOffsetRange(values=-196:709, indices=-196:709), IdOffsetRange(values=-68:837, indices=-68:837))
```

## 座標の意味

`imgw`は、`img`のインデックスに`inv(tform)`を適用した結果のインデックスを追跡します。これは、`imgw`のピクセルが`img`のピクセルとどのように整列するかを追跡するのに非常に便利です。

```jldoctest
julia> using ImageTransformations, TestImages, Interpolations

julia> img = testimage("lighthouse");

julia> imgr = imrotate(img, π/4);

julia> imgr_cropped = imrotate(img, π/4, axes(img));

julia> imgr[axes(img)...] == imgr_cropped # オフセットを手動で計算する必要はありません
true
```

!!! tip
    パフォーマンスを考慮すると、出力を`imgw[inds...]`で切り取るのではなく、`warp`に`inds`の位置引数を渡すことをお勧めします。


# 例: 2D回転

!!! note
    この例は、`tform`を構築し、`warp`を呼び出す方法のみを示しています。一般的な使用法としては、直接[`imrotate`](@ref)関数を使用することをお勧めします。


`img`の中心を回転します:

```jldoctest
julia> using ImageTransformations, CoordinateTransformations, Rotations, TestImages, OffsetArrays

julia> using OffsetArrays: IdOffsetRange

julia> img = testimage("lighthouse");

julia> axes(img)
(Base.OneTo(512), Base.OneTo(768))

julia> tfm = recenter(RotMatrix(-pi/4), center(img));

julia> imgw = warp(img, tfm);

julia> axes(imgw)
(IdOffsetRange(values=-196:709, indices=-196:709), IdOffsetRange(values=-68:837, indices=-68:837))
```
