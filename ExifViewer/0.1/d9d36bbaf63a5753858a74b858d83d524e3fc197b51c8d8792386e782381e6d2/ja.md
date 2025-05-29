read*tags(data::Vector{UInt8}; kwargs...}) read*tags(filepath::AbstractString; kwargs...) read_tags(io::IO; kwargs...)

入力ソースデータからEXIFタグを読み取ります。ソースデータにEXIFタグが含まれていない場合は、空の辞書を返します。

#### キーワード引数

  * `ifds::Union{Int,NTuple,UnitRange}` : EXIFタグを検索するIFD（画像ファイルディレクトリ）を定義します。デフォルトはすべてのifds、すなわち1:5です。
  * `read_all::Bool` : すべてのEXIFタグを読み取るかどうかを定義します。デフォルトでは、`read_all`はtrueです。
  * `tags::Vector{LibExif.ExifTag}` : `read_all`がfalseの場合に検索するタグを定義します。`read_all`がfalseの場合、検索する必要があるタグは手動で定義する必要があります。タグは複数の方法で提供できますが、各文字列がEXIFタグを表す文字列のベクターを提供することをお勧めします。すなわち、["`EXIF_TAG_FLASH_PIX_VERSION`", "`EXIF_TAG_ORIENTATION`"]
  * `extract_thumbnail::Bool` : サムネイルデータを読み取るかどうかを定義します。デフォルトでは、`extract_thumbnail`はfalseです。
  * `read_mnote::Bool` : mnote（MakerNote）タグデータを読み取るかどうかを定義します。デフォルトでは、`read_mnote`はfalseです。

検索可能なすべてのタグのリストは、こちらで確認できます: https://libexif.github.io/internals/exif-tag_8h.html

#### 例

```jl
julia> using TestImages, ExifViewer
julia> filepath = testimage("earth_apollo17.jpg", download_only=true)
julia> io = open(filepath, "r")
julia> read_tags(io; read_all=false, tags=["EXIF_TAG_FLASH_PIX_VERSION", "EXIF_TAG_ORIENTATION"])
Dict{Any, Any} with 2 entries:
"EXIF_TAG_FLASH_PIX_VERSION" => "FlashPix Version 1.0"
"EXIF_TAG_ORIENTATION"       => "Top-left"

julia> read_tags(filepath; read_all=false, tags=["EXIF_TAG_FLASH_PIX_VERSION", "EXIF_TAG_ORIENTATION"])
Dict{Any, Any} with 2 entries:
"EXIF_TAG_FLASH_PIX_VERSION" => "FlashPix Version 1.0"
"EXIF_TAG_ORIENTATION"       => "Top-left"

julia> data = read(filepath)
julia> read_tags(data, read_all=false, tags=["EXIF_TAG_FLASH_PIX_VERSION", "EXIF_TAG_ORIENTATION"])
Dict{Any, Any} with 2 entries:
  "EXIF_TAG_FLASH_PIX_VERSION" => "FlashPix Version 1.0"
  "EXIF_TAG_ORIENTATION"       => "Top-left"

```
