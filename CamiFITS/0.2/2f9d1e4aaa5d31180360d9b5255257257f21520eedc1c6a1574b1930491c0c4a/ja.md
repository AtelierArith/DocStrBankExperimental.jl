```
fits_apply_zero_offset(data)
```

`UInt` の値の範囲を `Int` の範囲にシフトするには、`data` から `BZERO` キーワードで指定された適切な整数オフセット値を *引き算* します。

注意: FITS 形式は *ネイティブの符号なし整数データ型* をサポートしていないため（`UInt8` を除く）、`UInt16`、`UInt32`、および `UInt64` の符号なし値は、それぞれ (正の) `BZERO` キーワード値で指定された適切な整数オフセットを *引き算* した後、ネイティブの符号付き整数である `Int16`、`Int32`、および `Int64` として保存されます。バイトデータ型 (`UInt8`) に関しては、符号付きバイト値 (`Int8`) をネイティブの符号なし値 (`UInt`) として保存するために、(負の) `BZERO` オフセット値を引き算する逆の手法が使用できます。

このメソッドは、`Int8`、`UInt16`、`UInt32`、および `UInt64` のネイティブ値をサポートしていないソフトウェアとの後方互換性を確保するために、データの保存に含まれ、使用されます。

#### 例:

```
julia> fits_apply_zero_offset(UInt32[0])
1-element Vector{Int32}:
 -2147483648

julia> fits_apply_zero_offset(Int8[0])
1-element Vector{UInt8}:
 0x80

julia> Int(0x80)
128
```
