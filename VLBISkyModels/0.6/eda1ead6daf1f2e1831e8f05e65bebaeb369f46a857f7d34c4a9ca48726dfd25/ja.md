```
imageviz(img::IntensityMap; scale_length = fieldofview(img.X/4), kwargs...)
```

`IntensityMap`のデフォルト画像可視化。

**もし `eltype(img) <: Real`** すなわち単一のストークスパラメータの画像であれば、これはJy/μas²の単位でカラーバー付きの画像をプロットします。このプロットは、REPLで`?image`と入力することでクエリできる`Makie.Image`型がサポートする任意の`kwargs`を受け入れます。

**もし `eltype(img) <: StokesParams`** すなわち完全偏光画像であれば、これは`polimage`を使用します。このプロットは、REPLで`?polimage`と入力することでクエリできる`PolImage`型がサポートする任意の`kwargs`を受け入れます。

!!! tip
    画像をカスタマイズするため、特定の軸を指定することをお勧めします。直接`image`と`polimage`を使用してください。


!!! warn
    この関数定義をロードするには、最初に`CairoMakie`をインポートする必要があります。

