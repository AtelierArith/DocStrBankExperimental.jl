```
magickinfo(file::Union{AbstractString,IO}, properties::Union{Tuple,AbstractVector})
```

画像 `file` を読み込み、要求された `properties` の値を含む Dict を返します。

# 例

```julia-repl
julia> magickinfo("IMG_6477.jpeg",
           ("exif:DateTime","exif:GPSLatitude","exif:GPSLatitudeRef",
            "exif:GPSLongitude","exif:GPSLongitudeRef","exif:GPSAltitude"))
Dict{String,Any} with 6 entries:
  "exif:GPSLongitudeRef" => "W"
  "exif:GPSLatitude"     => "44/1, 22/1, 2326/100"
  "exif:GPSLatitudeRef"  => "N"
  "exif:GPSLongitude"    => "71/1, 13/1, 5301/100"
  "exif:DateTime"        => "2020:01:22 13:17:41"
  "exif:GPSAltitude"     => "261189/757"
```
