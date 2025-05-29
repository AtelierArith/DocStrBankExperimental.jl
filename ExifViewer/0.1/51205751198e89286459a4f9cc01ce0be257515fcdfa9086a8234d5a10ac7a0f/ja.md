```markdown
write_tags(filepath::AbstractString; img::AbstractArray, tags::Dict{String,String})

EXIFタグをファイルパスに書き込みます（現在、jpegおよびjpgに対応しています）。

### キーワード引数

  * `filepath::AbstractString` : 画像とEXIFが書き込まれるファイルの名前。
  * `img::AbstractArray` : 上記のファイルパスにEXIFデータが書き込まれる画像配列。
  * `tags::Dict{String,String}` : libexifライブラリで定義されたEXIFタグとその対応する値。

### 例

```

jl julia> using ExifViewer, TestImages julia> img = testimage("mandrill")

julia> tags = Dict{String, String}(     "EXIF*TAG*MAKE"=>"Canon",     "EXIF*TAG*ORIENTATION"=>"Top-left",     "EXIF*TAG*X*RESOLUTION"=>"300",     "EXIF*TAG*Y*RESOLUTION"=>"300", ) julia> write_tags("test.jpg"; img, tags)

julia> read*tags("test.jpg") Dict{String, String} with 10 entries:   "EXIF*TAG*COLOR*SPACE"              => "Uncalibrated"   "EXIF*TAG*COMPONENTS*CONFIGURATION" => "Y Cb Cr -"   "EXIF*TAG*FLASH*PIX*VERSION"        => "FlashPix Version 1.0"   "EXIF*TAG*Y*RESOLUTION"             => "300"   "EXIF*TAG*ORIENTATION"              => "Top-left"   "EXIF*TAG*EXIF*VERSION"             => "Exif Version 2.1"   "EXIF*TAG*RESOLUTION*UNIT"          => "Inch"   "EXIF*TAG*MAKE"                     => "Canon"   "EXIF*TAG*YCBCR*POSITIONING"        => "Centered"   "EXIF*TAG*X*RESOLUTION"             => "300"

```

注意: 一部のタグはデフォルトで存在します（EXIFバージョン、FLASHPIXバージョンなど）、上記の例で確認できます。
```
