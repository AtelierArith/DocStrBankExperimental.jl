```
nmea_parse(nmea_string::AbstractString; validate_checksum=true)
```

NMEA文字列を解析し、対応するNMEAタイプを生成します。

この関数はNMEA文を入力として受け取り、`validate_checksum`が`true`に設定されている場合はチェックサムを検証し、その後、`NMEA_TYPES`に定義されたヘッダーとタイプに基づいて文を解析します。

# 引数

  * `nmea_string::AbstractString`: 解析するNMEA文。
  * `validate_checksum::Bool`: チェックサムを検証するかどうかを示すフラグ（デフォルトは`true`）。

# 戻り値

  * 適切なNMEAタイプのインスタンス。

# 例

```julia
result = nmea_parse("$GGA,123456,123.456,N,987.654,W,1,8,0.9,123.4,M,54.3,M,1,")
```
