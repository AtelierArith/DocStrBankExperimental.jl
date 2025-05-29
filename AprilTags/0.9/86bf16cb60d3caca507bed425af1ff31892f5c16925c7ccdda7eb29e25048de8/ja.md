```julia
calcCornerProjectionsAprilTags!(
    cimg_,
    tags_;
    tagList,
    taglength,
    f_width,
    f_height,
    c_width,
    c_height,
    s,
    VERT,
    HORI,
    boardPattern,
    dodraw
)

```

Aprilグリッドキャリブレーションヘルパー関数は、単一画像のコストを組み立てるためのものです。この関数は、コスト関数がどのように構成されているか、またキャリブレーションのパフォーマンスを示すために画像上にコーナーポイントを描画するためにも使用できます。詳細については[`calcCalibResidualAprilTags!`](@ref)を参照してください。
