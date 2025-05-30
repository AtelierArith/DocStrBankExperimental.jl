```
magickinfo(file::Union{AbstractString,IO})
```

画像 `file` を読み込み、画像ファイルのプロパティデータを説明する文字列の配列を返します。

# 例

```julia-repl
julia> p = magickinfo("Image.jpeg")
63-element Array{String,1}:
 "date:create"
 "date:modify"
 "exif:ApertureValue"
 "exif:BrightnessValue"
 "exif:ColorSpace"
 "exif:ComponentsConfiguration"
 "exif:DateTime"
 "exif:DateTimeDigitized"
 "exif:DateTimeOriginal"
 "exif:ExifImageLength"
 "exif:ExifImageWidth"
 "exif:ExifOffset"
 "exif:ExifVersion"
 ⋮
 "exif:thumbnail:JPEGInterchangeFormat"
 "exif:thumbnail:JPEGInterchangeFormatLength"
 "exif:thumbnail:ResolutionUnit"
 "exif:thumbnail:XResolution"
 "exif:thumbnail:YResolution"
 "exif:WhiteBalance"
 "exif:XResolution"
 "exif:YCbCrPositioning"
 "exif:YResolution"
 "jpeg:colorspace"
 "jpeg:sampling-factor"
 "unknown"a
```
