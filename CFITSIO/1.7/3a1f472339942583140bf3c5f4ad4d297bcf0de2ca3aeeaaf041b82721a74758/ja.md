```
fits_read_atblhdr(f::FITSFile, maxdim::Integer = 99)
```

ASCIIテーブルHDUのヘッダーを読み込みます。ここで、`maxdim`は読み込む最大列数を表します。この関数は、バイト単位の行の長さ、行数、列数、列名を`Vector{String}`として、各列へのバイトオフセット、TFORMn値を`Vector{String}`として、TUNITn値を`Vector{String}`として、そして`EXTNAME::String`キーワード（存在する場合）を返します。
