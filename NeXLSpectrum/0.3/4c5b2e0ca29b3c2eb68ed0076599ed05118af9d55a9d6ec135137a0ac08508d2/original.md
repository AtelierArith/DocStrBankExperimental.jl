```
readrplraw(rplfilename::AbstractString, rawfilename::AbstractString)
readrplraw(rplio::IO, rawio::IO)
```

Read a RPL/RAW file pair from IO or filename into an Array obect.  The reader supports :bigendian, :littleendian ordering and :vector or :image alignment.  Since the Array can be very large it is beneficial to release and collected the associated memory when you are done with the data by assigning `nothing` to the variable (or allowing it to go out of scope) and then calling `GC.gc()` to force a garbage collection.

```
* Ordering: The individual data items may be in `:littleendian` or `:bigendian`.
** `:littleendian` => Intel/AMD and others
** `:bigendian` => ARM/PowerPC/Motorola
* Alignment:  The data in the file can be organized as `:vector` or `:image`.  However, the data will be
```

reorganized into 'vector' format when returned as a Array.     **`:vector` => Spectrum/data vector as contiguous blocks by pixel     ** `:image` => Each channel of data organized in image planes     * Data types: signed/unsigned 8/16/32-bit integers or 16-bit/32-bit/64-bit floats

```
readrplraw(filenamebase::AbstractString)::Array{<:Real}
```

Read the files filenamebase*".rpl" and filenamebase*".raw" into an Array.  Maintains the data type of the values in the RAW file.

#### Standard LISPIX Parameters in .rpl File

.rpl files consist of 9 lines.  Each line consists of a 'key'<tab>'value' where there is one and only one tab and possibly other space between the parameter name and parameter value. Parameter names are case-insensitive. The first line in the files is "key<tab>value".  Subsequent lines contain the keys and values described in this table.

| **key**     | **value** | **description**                         |
|:----------- | ---------:|:--------------------------------------- |
| width       |       849 | pixels per row       integer            |
| height      |       846 | rows                 integer            |
| depth       |      4096 | images or spec pts   integer            |
| offset      |         0 | bytes to skip        integer            |
| data-length |         1 | bytes per pixel      1, 2, 4, or 8      |
| data-type   |  unsigned | signed, unsigned, or float              |
| byte-order  | dont-care | big-endian, little-endian, or dont-care |
| record-by   |    vector | image, vector, or dont-care             |

This .rpl file indicates the image is 849 pixels wide and 846 pixels high, with 4096 levels in the depth dimension.
