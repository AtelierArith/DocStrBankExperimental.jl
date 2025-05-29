```
save(filename::AbstractString,
     P::Union{Plot2D,Plot3D};
     runasy=true,
     forcepdf=false)
```

Asymptote 図を保存します。`filename` に拡張子 `.asy` がある場合、asy ファイルとともに補助データファイルが保存されます。

`filename` に拡張子 `.pdf`、`.svg` または `.png` がある場合、結果の画像ファイルのみが `filename` の場所に保存されます。
