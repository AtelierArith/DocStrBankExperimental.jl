```
result::StatsBase.Histogram =
    bin_cmd_smooth(colors,
                   mags,
                   color_err,
                   mag_err;
                   weights = ones(promote_type(eltype(colors), eltype(mags)),
                                  size(colors)),
                   edges   = nothing,
                   xlim    = extrema(colors),
                   ylim    = extrema(mags),
                   nbins   = nothing,
                   xwidth  = nothing,
                   ywidth  = nothing)
```

`StatsBase.Histogram` 型を返し、点が提供された `color_err` と `mag_err` によって与えられた幅の 2D 非対称ガウスを使用して平滑化されたヘス図を含み、与えられた `weights` によって重み付けされます。これらの配列はすべて同じサイズでなければなりません。これは、各点が自分の確率分布によって広がる KDE に似ています。キーワード引数は [`bin_cmd_smooth`](@ref) および [`StarFormationHistories.calculate_edges`](@ref) で説明されている通りです。これを `PyPlot` でプロットするには、`plt.imshow(result.weights', origin="lower", ...)` を実行する必要があります。

推奨される使用法は、まず [`bin_cmd`](@ref) を使用して観測データのヒストグラムを作成し、次に得られたヒストグラムビンを `edges` キーワードを使用して [`bin_cmd_smooth`](@ref) および [`partial_cmd_smooth`](@ref) に渡して平滑化された等時線モデルを構築することです。
