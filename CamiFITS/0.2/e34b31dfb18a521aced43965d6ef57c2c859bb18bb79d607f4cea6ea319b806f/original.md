```
cast_FITS_header(dataobject::FITS_dataobject)
```

Create the [`FITS_header`](@ref) object from the dataobject. The  dataobject-input mode is used by [`fits_create`](@ref) to ceate the header object as part of creating the [`FITS`](@ref) object starting from Julia data  input.

#### Example:

```
julia> data = [11 21 31; 12 22 23; 13 23 33];

julia> d = cast_FITS_dataobject("image", data);

julia> h = cast_FITS_header(d);

julia> h.map
Dict{String, Int64} with 7 entries:
  "BITPIX"   => 2
  "NAXIS2"   => 5
  "XTENSION" => 1
  "NAXIS1"   => 4
  ""         => 36
  "NAXIS"    => 3
  "END"      => 6
```

```
cast_FITS_header(record::Vector{String})
```

Create the [`FITS_header`](@ref) object from a block of (a multiple of) 36  single-record strings (of 80 printable ASCII characters). The record-input mode is used by [`fits_read`](@ref) after reading the header records from disk  (see casting diagram above).

#### Example:

```
julia> record = [rpad("KEYWORD$i",8) * "'" * rpad("$i",70) * "'" for i=1:3];

julia> blanks = [repeat(' ', 80) for i = 1:36-length(record)];

julia> append!(record, blanks);         # to conform to the FITS standard

julia> h = cast_FITS_header(record);

julia> h.map
Dict{String, Int64} with 4 entries:
  "KEYWORD3" => 3
  "KEYWORD2" => 2
  "KEYWORD1" => 144
  ""         => 36
```
