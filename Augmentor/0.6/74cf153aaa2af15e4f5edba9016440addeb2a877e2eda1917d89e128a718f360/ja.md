```
augment!(out, img, pipeline) -> out
```

与えられた `pipeline` の操作を画像 `img` に順次適用し、結果の画像を事前に割り当てられたパラメータ `out` に書き込みます。便利なことに、`out` は関数の戻り値でもあります。

```julia
img = testpattern()
out = similar(img)
augment!(out, img, FlipX() |> FlipY())
```

パラメータ `img` は単一の画像であるか、複数の画像のタプルであることができます。`img` が画像のタプルである場合、パラメータ `out` は同じ長さと順序のタプルでなければなりません。詳細については [`augment`](@ref) を参照してください。

```julia
imgs = (testpattern(), Gray.(testpattern()))
outs = (similar(imgs[1]), similar(imgs[2]))
augment!(outs, imgs, FlipX() |> FlipY())
```

パラメータ `pipeline` は `Augmentor.Pipeline`、`Augmentor.Operation` のタプル、または単一の `Augmentor.Operation` であることができます。

```julia
img = testpattern()
out = similar(img)
augment!(out, img, FlipX() |> FlipY())
augment!(out, img, (FlipX(), FlipY()))
augment!(out, img, FlipX())
```
