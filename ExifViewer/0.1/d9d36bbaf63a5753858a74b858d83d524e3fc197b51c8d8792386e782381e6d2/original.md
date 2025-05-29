read*tags(data::Vector{UInt8}; kwargs...}) read*tags(filepath::AbstractString; kwargs...) read_tags(io::IO; kwargs...)

Read EXIF tags from the input source data. Return an empty dictionary if the source data doesn't contain EXIF tags.

#### Keyword Arguments

  * `ifds::Union{Int,NTuple,UnitRange}` : Defines which IFD(Image file directory) to search in for the EXIF tags. Default is all ifds i.e. 1:5.
  * `read_all::Bool` : Defines if all EXIF tags are to be read or not. By default, `read_all` is true.
  * `tags::Vector{LibExif.ExifTag}` : Defines which tags to search, in case `read_all` is false. When `read_all` is false, tags that need to be searched need to defined manually. Tags can be provided using bunch of methods but its suggested to supply a vector of strings with each string representing a EXIF tag i.e. ["`EXIF_TAG_FLASH_PIX_VERSION`", "`EXIF_TAG_ORIENTATION`"]
  * `extract_thumbnail::Bool` : Defines whether to read the thumbnail data or not. By default, `extract_thumbnail` is false.
  * `read_mnote::Bool` : Defines whether to read the mnote(MakerNote) tags data or not. By default, `read_mnote` is false.

List of all available tags to search is available here: https://libexif.github.io/internals/exif-tag_8h.html

#### Examples

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
