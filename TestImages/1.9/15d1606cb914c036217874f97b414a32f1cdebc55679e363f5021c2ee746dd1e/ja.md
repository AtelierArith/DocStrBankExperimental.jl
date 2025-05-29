```
img = testimage(filename; download_only=false, [ops...]
```

`filename` に部分一致する画像をDIP3E教科書から大文字小文字を区別せずに読み込みます。

`download_only=true` の場合、フルファイルパスが返されます。その他のキーワード `ops` は `FileIO.load` を通じて画像IOバックエンドに渡されます。

# 例

```julia
julia> using TestImages
julia> img = testimage_dip3e("cameraman") # Fig0222(b)(cameraman).tif に一致
julia> img = testimage_dip3e("fig0222(a)")
```

!!! note "ライセンス"
    画像が個人的な教育または研究目的以外で使用される場合、© 画像の所有者からの許可が必要です。著作権ファイルを参照してください: https://www.imageprocessingplace.com/DIP-3E/dip3e_copyrights.htm。


DIP3E: "Digital Image Processing, 3rd edition" by Rafael C. Gonzalez and Richard E. Woods
