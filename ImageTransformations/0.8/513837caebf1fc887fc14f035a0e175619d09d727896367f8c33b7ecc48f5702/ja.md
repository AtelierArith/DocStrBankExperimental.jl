```
warp(img, tform, [indices], [degree = Linear()], [fill = NaN]) -> imgw
```

`img`の座標を変換し、新しい`imgw`を返します。これは`imgw[I] = img[tform(I)]`を満たします。このアプローチはバックワードモードのワーピングとして知られています。変換`tform`は`SVector`を入力として受け入れる必要があります。さまざまな変換を作成するための便利なパッケージは[CoordinateTransformations.jl](https://github.com/FugroRoames/CoordinateTransformations.jl)です。

# 再構成スキーム

ワーピング中、`img`の値は、ピクセルの格子上にない任意の位置`tform(I)`で再構成される必要があります。この再構成がどのように行われるかは、`img`のタイプとオプションのパラメータ`degree`によって異なります。

`img`が通常の配列である場合、オン・グリッドのbスプライン補間が使用されます。使用するbスプラインの次数は、パラメータ`degree`で設定できます。たとえば、線形補間には`degree = Linear()`、最近傍補間には`degree = Constant()`、二次補間には`degree = Quadratic(Flat())`を使用できます。

`tform(I)`が元の`img`の外部のインデックスにマッピングされる場合、それらの位置は値`fill`に設定されます（要素タイプがサポートしている場合はデフォルトで`NaN`、そうでない場合は`0`）。パラメータ`fill`は、`Flat()`、`Periodic()`、または`Reflect()`などの外挿スキームも受け入れます。

再構成スキームの制御をより細かく行いたい場合は、[Interpolations.jl](https://github.com/JuliaMath/Interpolations.jl)から`AbstractInterpolation`または`AbstractExtrapolation`として`img`を渡してください。

キーワード`method`は、Interpolations.jlの任意のInterpolationTypeまたはDegreeも受け入れ、使用される補間方法を設定するためにその次数のBSpline補間を定義するために使用されます。

# 座標の意味

出力配列`imgw`は、`img`のインデックスに`inv(tform)`を適用した結果得られるインデックスを持っています。これは、`imgw`のピクセルが`img`のピクセルとどのように整列するかを追跡するのに非常に便利です。

単純な配列が必要な場合は、`parent(imgw)`を使用してカスタムインデックスを「ストリップ」できます。

# 例：2D回転（画像についてはJuliaImagesのドキュメントを参照）

```
julia> using Images, CoordinateTransformations, Rotations, TestImages, OffsetArrays

julia> img = testimage("lighthouse");

julia> axes(img)
(Base.OneTo(512),Base.OneTo(768))

# `img`の中心を回転
julia> tfm = recenter(RotMatrix(-pi/4), center(img))
AffineMap([0.707107 0.707107; -0.707107 0.707107], [-196.755,293.99])

julia> imgw = warp(img, tfm);

julia> axes(imgw)
(-196:709,-68:837)

# あるいは、画像自体の原点を指定
julia> img0 = OffsetArray(img, -30:481, -384:383);  # 画像の上部近くに原点

julia> rot = LinearMap(RotMatrix(-pi/4))
LinearMap([0.707107 -0.707107; 0.707107 0.707107])

julia> imgw = warp(img0, rot);

julia> axes(imgw)
(-293:612,-293:611)

julia> imgr = parent(imgw);

```

jldoctest using ImageTransformations, CoordinateTransformations, Rotations, TestImages, OffsetArrays using OffsetArrays: IdOffsetRange img = testimage("lighthouse") # axes (1:512, 1:768)

tfm = recenter(RotMatrix(-pi/4), center(img)) imgw = warp(img, tfm)

axes(imgw)

# 出力

(IdOffsetRange(values=-196:709, indices=-196:709), IdOffsetRange(values=-68:837, indices=-68:837)) ```
