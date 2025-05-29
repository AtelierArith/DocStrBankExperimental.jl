指定された都市の時間ごとの過去の気温、降雨、降雪、相対湿度、風速、太陽データをSQLiteデータベースに保存します（"start*date" と "end*date" の間）。各気象変数は別々のテーブルとして保存されます。データベース自体は、このリポジトリのルートにある "export" フォルダに保存されます。

# 引数

  * `city::String` : 有効な都市名、例: "Oslo", "Paris", "Amsterdam" など。
  * `i_row::Int64` : 指定された場所に対して複数の一致がある場合、印刷されたDataFrameから行インデックスを提供することで希望のタイムゾーンを選択します。デフォルトは1に設定されています。
  * `start_date::String` : ISO8601日付形式の開始日、例: "2023-02-01"
  * `end_date::String` : ISO8601日付形式の終了日、例: "2023-02-25"

# オプションのキーワード

  * `lat::Float64` : 場所の地理的WGS84座標 (°S < 0, °N > 0)
  * `long::Float64` : 場所の地理的WGS84座標 (°W < 0, °E > 0)

# 例

```julia-repl
julia> export_to_sqlite("Veldhoven", start_date = "2022-01-01", end_date = "2022-01-31")
```
