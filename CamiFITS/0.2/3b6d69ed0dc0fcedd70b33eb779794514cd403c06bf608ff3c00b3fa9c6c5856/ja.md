```
fits_insert_key!(f::FITS, hduindex::Int, cardindex::Int, key::String, val::Any, com::String)
```

指定された 'key'、'value'、および 'comment' のために、`f.hdu[hduindex].header.card` の位置 `cardindex` に1つ以上の [`FITS_card`] を挿入します。すなわち、[`FITS`](@ref) オブジェクト 'f' の [`FITS_HDU`](@ref)`[hduindex]` の [`FITS_header`](@ref) のレコードスタックに挿入します。

注: `cardindex` を指定せずに挿入するには、[`fits_add_key!`](@ref) を使用してください。

#### 例:

```
julia> filnam = "minimal.fits";

julia> f = fits_create(filnam; protect=false);

julia> fits_insert_key!(f, 1, 3, "KeYNEw1", true, "This is the new key");

julia> fits_info(f;nr=true);

File: minimal.fits
hdu: 1
hdutype: 'PRIMARY '
DataType: Any
Datasize: (0,)

  nr | Metainformation:
---------------------------------------------------------------------------------------
   1 | SIMPLE  =                    T / file does conform to FITS standard
   2 | BITPIX  =                   64 / number of bits per data pixel
   3 | KEYNEW8 =                    T / This is the new key
   4 | NAXIS   =                    1 / number of data axes
   5 | NAXIS1  =                    0 / length of data axis 1
   6 | EXTEND  =                    T / FITS dataset may contain extensions
   7 | END
```
