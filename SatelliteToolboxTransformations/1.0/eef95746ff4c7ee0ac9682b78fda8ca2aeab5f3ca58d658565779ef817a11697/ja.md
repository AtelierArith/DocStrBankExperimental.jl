```
read_iers_eop(filename::String[, data_type]) -> EopIau1980 | EopIau2000A
```

ファイル `filename` から IERS EOP データを読み込みます。ユーザーはデータがモデル IAU 1980 (`data_type = Val(:IAU1980)`) に関連しているか、デフォルトとして、またはモデル IAU 2000A (`data_type = Val(:IAU2000A)`) に関連しているかを指定する必要があります。

!!! note
    入力ファイルは **IERS によって提供された CSV 形式と正確に同じでなければなりません**。以下のコマンドを使用してダウンロードできます：

      * IAU 1980

        curl -O https://datacenter.iers.org/data/csv/finals.all.csv   wget https://datacenter.iers.org/data/csv/finals.all.csv
      * IAU 2000A

        curl -O https://datacenter.iers.org/data/csv/finals2000A.all.csv   wget https://datacenter.iers.org/data/csv/finals2000A.all.csv


# 戻り値

  * [`EopIau1980`](@ref) または [`EopIau2000A`](@ref)、`data_type` に応じて：EOP の補間を持つオブジェクト。補間インデックスはジュリアンデイに設定されています。

```
