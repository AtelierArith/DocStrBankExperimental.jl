```
TiledView(data::F, tile_size::NTuple{N,Int}, 
          tile_overlap::NTuple{N,Int} = tile_size .* 0, 
          tile_center::NTuple{M,Int} = (mod.(tile_size,2) .+ 1)
          ; pad_value::T, keep_center=true)
```

Creates an 2N dimensional view of the data by tiling the N-dimensional data as  specified by tile*size, tile*overlap and optionally tile_center.

## Arguments

  * `data`: the input data to decompose into a TiledView. No copies are made for the `TiledView` and the raw data can be accessed via `.parent`.
  * `tile_size`: A Tuple describing the size of each tile. This size will form the first N dimensions of the result of `size(myview)`. The second N dimensions refer to N-dimensional tile numbering.
  * `tile_overlap`: Tuple specifying the overlap between successive tiles in voxels. This implicitely defines the pitch between tiles as `(tile_size .- tile_overlap)`.

## Keyword Argument

  * `pad_value`: Specifies the answer that is returned when get_index is applied to a position outside the source array.
  * `keep_center`:  This boolean specifies whether the center of the parent `data` will be aligned with the center of the central tile. If `false`, the first tile starts at offset zero.
  * `tile_center`:  Only used if `keep_center` is true. It defines the center position in the central tile. The default is `tile_size .÷ 2 .+1`.

# Examples

```jldoctest TiledView
julia> a = TiledView(reshape(1:49,(7,7)), (4, 4),(1, 1));

julia> a.parent
7×7 reshape(::UnitRange{Int64}, 7, 7) with eltype Int64:
 1   8  15  22  29  36  43
 2   9  16  23  30  37  44
 3  10  17  24  31  38  45
 4  11  18  25  32  39  46
 5  12  19  26  33  40  47
 6  13  20  27  34  41  48
 7  14  21  28  35  42  49

julia> size(a)
(4, 4, 3, 3)
```
