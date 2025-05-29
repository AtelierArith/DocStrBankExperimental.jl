```
fits_parse_table(hdu::FITS_HDU; byrow=true)
```

Parse `FITS_TABLE` (ASCII table) into a Vector of its rows/columns for further processing by the user. Default formatting in ISO 2004 FORTRAN data format specified by keys "TFORMS1" - "TFORMSn"). Display formatting in ISO 2004 FORTRAN data format ("TDISP1" - "TDISPn") prepared for user editing.

#### Example:

```
julia> filnam = "foo.fits";
    
julia> fits_create(filnam; protect=false);
    
julia> data = [[true, 0x6c, 1081, 0x0439, 1081, 0x00000439, 1081, 0x0000000000000439, 1.23, 1.01f-6, 1.01e-6, 'a', "a", "abc"],
               [false, 0x6d, 1011, 0x03f3, 1011, 0x000003f3, 1011, 0x00000000000003f3, 123.4, 3.01f-6, 3.001e-5, 'b', "b", "abcdef"]];
    
julia> f = fits_extend(filnam, data; hdutype="table");
    
julia> fits_parse_table(f.hdu[2]; byrow=true)                                                                                                                                                                  
2-element Vector{Vector{Any}}:
     [1, 108, 1081, 1081, 1081, 1081, 1081, 1081, 1.23, 1.01e-6, 1.01e-6, "a", "a", "   abc"]
     [0, 109, 1011, 1011, 1011, 1011, 1011, 1011, 123.4, 3.01e-6, 3.001e-5, "b", "b", "abcdef"]
    
julia> fits_parse_table(f.hdu[2]; byrow=false)
14-element Vector{Any}:
 [1, 0]
 [108, 109]
 [1081, 1011]
 [1081, 1011]
 [1081, 1011]
 [1081, 1011]
 [1081, 1011]
 [1081, 1011]
 [1.23, 123.4]
 [1.01e-6, 3.01e-6]
 [1.01e-6, 3.001e-5]
 ["a", "b"]
 ["a", "b"]
 ["   abc", "abcdef"]
    
julia> rm(filnam)
```
