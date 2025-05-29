```
img1, img2 = AstroImage(filename::AbstractString, exts)
```

FITSファイル`filename`から複数の画像HDU`exts`をAstroImageとして読み込みます。`exts`はタプル、範囲、:、または整数の配列でなければなりません。`exts`にリストされたすべてのHDUは画像HDUでなければならず、そうでない場合はエラーが発生します。

例:

```julia
img1, img2 = AstroImage("abc.fits", (1,3)) # 最初と3番目のHDUを画像として読み込みます。
imgs = AstroImage("abc.fits", 1:3) # 最初の3つのHDUを画像として読み込みます。
imgs = AstroImage("abc.fits", :) # すべてのHDUを画像として読み込みます。
```
