```
readbla(filename)
```

固定幅のASCIIファイル用のBlaise仕様ファイルを読み込みます。'Varspec'オブジェクトのベクターを返します。

Blaise仕様ファイルの簡単な例は次のようになります。

```
datamodel testbla
 Fields
    var1        : integer[9]
    var2        : string[8]
    dummy[2]
    var3        : Real[8, 2]
    vars        : Array[2010..2050] of STRING[4]
endmodel
```
