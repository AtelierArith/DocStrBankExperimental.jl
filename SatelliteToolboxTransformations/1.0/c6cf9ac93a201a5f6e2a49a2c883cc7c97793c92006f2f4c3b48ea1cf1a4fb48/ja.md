```
fetch_iers_eop([data_type]; kwargs...) -> EopIau1980 | EopIau2000A
```

IERS EOP C04データをダウンロードして解析します。データタイプは`data_type`で指定されます。サポートされている値は次のとおりです。

  * `Val(:IAU1980)`: IERS EOP C04 IAU1980データを取得します。
  * `Val(:IAU2000A)`: IERS EOP C04 IAU2000Aデータを取得します。

`data_type`が省略された場合、デフォルトは`Val(:IAU1980)`になります。

この関数は、EOPパラメータの補間を含む構造体（`EopIau1980`[@ref]または`EopIau2000A`[@ref]、`data_type`に応じて）を返します。補間インデックスはユリウス日付に設定されています。

# キーワード

  * `force_download::Bool`: EOPファイルが存在し、7日未満の古さであれば、再度ダウンロードされません。このキーワードを`true`に設定することで新しいダウンロードを強制できます。 (**デフォルト** = `false`)
  * `url::String`: EOPファイルのURL。

```julia-repl
julia> eop = fetch_iers_eop()
[ Info: Downloading file 'EOP_IAU1980.TXT' from 'https://datacenter.iers.org/data/csv/finals.all.csv'...
EopIau1980:
     Data │ Timespan
 ─────────┼──────────────────────────────────────────────
        x │ 1973-01-02T00:00:00 -- 2022-05-28T00:00:00
        y │ 1973-01-02T00:00:00 -- 2022-05-28T00:00:00
  UT1-UTC │ 1973-01-02T00:00:00 -- 2022-05-28T00:00:00
      LOD │ 1973-01-02T00:00:00 -- 2021-05-19T00:00:00
       dψ │ 1973-01-02T00:00:00 -- 2021-08-05T00:00:00
       dϵ │ 1973-01-02T00:00:00 -- 2021-08-05T00:00:00

julia> eop = fetch_iers_eop(Val(:IAU2000A))
[ Info: Downloading file 'EOP_IAU2000A.TXT' from 'https://datacenter.iers.org/data/csv/finals2000A.all.csv'...
EopIau2000A:
     Data │ Timespan
 ─────────┼──────────────────────────────────────────────
        x │ 1973-01-02T00:00:00 -- 2022-05-28T00:00:00
        y │ 1973-01-02T00:00:00 -- 2022-05-28T00:00:00
  UT1-UTC │ 1973-01-02T00:00:00 -- 2022-05-28T00:00:00
      LOD │ 1973-01-02T00:00:00 -- 2021-05-19T00:00:00
       dX │ 1973-01-02T00:00:00 -- 2021-08-05T00:00:00
       dY │ 1973-01-02T00:00:00 -- 2021-08-05T00:00:00
```
