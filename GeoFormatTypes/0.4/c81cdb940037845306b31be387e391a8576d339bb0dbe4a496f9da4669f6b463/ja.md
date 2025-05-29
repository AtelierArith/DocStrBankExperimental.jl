```
EPSG <: CoordinateReferenceSystemFormat

EPSG(input)
```

EPSGコードは、EPSG空間参照システムレジストリからの座標参照システムを表します。

文字列入力は「EPSG:」で始まる必要があります。`EPSG`は、`convert`を使用して`Int`または`String`に変換することができ、ArchGDAL.jlがロードされているときは他の`CoordinateReferenceSystemFormat`にも変換できます。
