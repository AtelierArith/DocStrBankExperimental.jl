```
fits_read_btblhdr(f::FITSFile, maxdim::Integer = 99)
```

バイナリテーブルHDUのヘッダーを読み取ります。ここで、`maxdim`は読み取る最大列数を表します。この関数は、行数、列数、列名を`Vector{String}`として、TFORMn値を`Vector{String}`として、TUNITn値を`Vector{String}`として、そして`EXTNAME::String`および`PCOUNT::Int`キーワードを返します。
