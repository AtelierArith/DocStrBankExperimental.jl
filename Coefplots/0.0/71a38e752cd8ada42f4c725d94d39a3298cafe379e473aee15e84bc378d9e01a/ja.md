```
CaptionStyle
```

これは `Coefplot.xticklabel`、`Coefplot.yticklabel`、`Coefplot.xlabel.captionstyle`、`Coefplot.ylabel.captionstyle`、`Coefplot.title.captionstyle`、`Coefplot.note.captionstyle` を入力します。

# コンストラクタ

```julia
CaptionStyle(;font=missing, size=missing, rotate=missing)
```

# キーワード引数

  * `font::Union{Symbol, String, Missing}` はフォントのT1コードを含みます
  * `size::Union{Real, Missing}` はフォントのサイズ（pt単位）です。
  * `rotate::Union{Real, Missing}` はキャプションの反時計回りの回転角度です。
