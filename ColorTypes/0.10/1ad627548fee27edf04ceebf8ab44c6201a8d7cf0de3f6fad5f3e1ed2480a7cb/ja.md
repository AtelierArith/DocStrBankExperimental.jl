ColorTypes の概要：

型階層：

```
                          Colorant{T,N}
             Color{T,N}                    TransparentColor{C,T,N}
     AbstractRGB{T}                  AlphaColor{C,T,N}  ColorAlpha{C,T,N}
```

具体的な型：

  * `RGB`, `BGR`, `XRGB`, `RGBX`, `RGB24` はすべて `AbstractRGB` のサブタイプです
  * `HSV`, `HSL`, `HSI`, `XYZ`, `xyY`, `Lab`, `LCHab`, `Luv`, `LCHuv`, `DIN99`, `DIN99d`, `DIN99o`, `LMS`, `YIQ`, `YCbCR` は `Color{T,3}` のサブタイプです
  * ほとんどのこれらの型に対するアルファチャネルの類似物として `ARGB` と `RGBA` が存在します（`RGB24` のような例外もありますが、これは `ARGB32` を持っています）
  * グレースケール型 `Gray` と `Gray24` （`Color{T,1}` のサブタイプ）および対応する透明型 `AGray`, `GrayA`, `AGray32`
  * 特性関数 `eltype`, `length`, `alphacolor`, `coloralpha`, `color_type`, `base_color_type`, `base_colorant_type`, `ccolor`
  * ゲッター `red`, `green`, `blue`, `alpha`, `gray`, `comp1`, `comp2`, `comp3`

特定の型や関数についての詳細情報を得るには `?` を使用してください。
