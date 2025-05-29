```
cast_FITS_header(dataobject::FITS_dataobject)
```

データオブジェクトから[`FITS_header`](@ref)オブジェクトを作成します。データオブジェクト入力モードは、[`fits_create`](@ref)によって、Juliaデータ入力から[`FITS`](@ref)オブジェクトを作成する際にヘッダーオブジェクトを作成するために使用されます。

#### 例:

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

36の倍数の80の印刷可能なASCII文字からなる単一レコード文字列のブロックから[`FITS_header`](@ref)オブジェクトを作成します。レコード入力モードは、ディスクからヘッダーレコードを読み取った後に[`fits_read`](@ref)によって使用されます（上記のキャスティングダイアグラムを参照）。

#### 例:

```
julia> record = [rpad("KEYWORD$i",8) * "'" * rpad("$i",70) * "'" for i=1:3];

julia> blanks = [repeat(' ', 80) for i = 1:36-length(record)];

julia> append!(record, blanks);         # FITS標準に準拠するため

julia> h = cast_FITS_header(record);

julia> h.map
Dict{String, Int64} with 4 entries:
  "KEYWORD3" => 3
  "KEYWORD2" => 2
  "KEYWORD1" => 144
  ""         => 36
```
