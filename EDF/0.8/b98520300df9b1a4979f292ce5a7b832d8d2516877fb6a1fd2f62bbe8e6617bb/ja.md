```
EDF.File(io::IO)
```

指定された `io` をラップする `EDF.File` インスタンスを返し、`io` から読み取られた EDF 形式のファイル、信号、および注釈ヘッダーも返します。このコンストラクタはヘッダーのみを読み取り、その後のサンプルデータは読み取りません。返された `EDF.File` に `io` からその後のサンプルデータを読み込むには、`EDF.read!(file)` を呼び出してください。
