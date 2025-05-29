write_tags(filepath::AbstractString; img::AbstractArray, tags::Dict{String,String})

Write EXIF tags to a filepath(currently support for jpeg and jpg available). 

### Keyword Arguments

  * `filepath::AbstractString` : Name of the file to which image and exif is written.
  * `img::AbstractArray` : Image Array whose exif data is being written to the filepath mentioned above.
  * `tags::Dict{String,String}` : EXIF tags and their corresponding values as defined in libexif library

### Examples

```jl
julia> using ExifViewer, TestImages
julia> img = testimage("mandrill")

julia> tags = Dict{String, String}(
    "EXIF_TAG_MAKE"=>"Canon",
    "EXIF_TAG_ORIENTATION"=>"Top-left",
    "EXIF_TAG_X_RESOLUTION"=>"300",
    "EXIF_TAG_Y_RESOLUTION"=>"300",
)
julia> write_tags("test.jpg"; img, tags)

julia> read_tags("test.jpg")
Dict{String, String} with 10 entries:
  "EXIF_TAG_COLOR_SPACE"              => "Uncalibrated"
  "EXIF_TAG_COMPONENTS_CONFIGURATION" => "Y Cb Cr -"
  "EXIF_TAG_FLASH_PIX_VERSION"        => "FlashPix Version 1.0"
  "EXIF_TAG_Y_RESOLUTION"             => "300"
  "EXIF_TAG_ORIENTATION"              => "Top-left"
  "EXIF_TAG_EXIF_VERSION"             => "Exif Version 2.1"
  "EXIF_TAG_RESOLUTION_UNIT"          => "Inch"
  "EXIF_TAG_MAKE"                     => "Canon"
  "EXIF_TAG_YCBCR_POSITIONING"        => "Centered"
  "EXIF_TAG_X_RESOLUTION"             => "300"
```

Note: some tags are present by default like EXIF version, FLASHPIX version etc as can be seen in example above.
