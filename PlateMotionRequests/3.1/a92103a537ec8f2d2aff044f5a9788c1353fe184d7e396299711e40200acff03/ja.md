```
write_platemotion(file, table)
```

`file`にタブ区切りのテキスト列またはNetCDFとしてプレート運動テーブルを書き込みます。`file`が`.nc`拡張子で終わる場合、**実験的**なNetCDFメソッドが使用されます。タブ区切りの出力の場合、最初の行は列名を含むヘッダーです。

テーブルヘッダーが認識されない場合や、不規則にサンプリングされたデータのNetCDFファイルを書き込もうとした場合、`PlateMotionRequests.WriteError`がスローされます。

!!! note
    緯度または経度値の不規則なサンプリングは、NetCDF出力ではサポートされていません。


参照: [`read_platemotion`](@ref).
