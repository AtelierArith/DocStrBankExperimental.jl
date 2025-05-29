```
write(filename::String, blafilename::String, table)
```

テーブルを固定幅のASCIIファイルに書き込みます。blafileにはBlaise形式でのファイルの仕様が含まれています。

データ型、長さ、および関連する場合は仕様から小数点を使用して、必要な幅を使用して単一の値を書き込むための変換関数が生成されます。String、Integer、Real、およびDummyの場合、*makewrite*によって変換関数が生成されます。他のデータ型については、必要なジェネレーターを提供する必要があります。
