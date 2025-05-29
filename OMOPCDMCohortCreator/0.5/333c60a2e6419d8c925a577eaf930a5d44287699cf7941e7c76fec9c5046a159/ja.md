GetDatabaseYearRange(; tab = observation_period)

データベースから利用可能なデータの年を見つけるためのSQLを返します。

# キーワード引数:

  * `tab` - 観察期間テーブルを表す `SQLTable`；デフォルトは `observation_period`

# 戻り値

  * `year_range::NamedTuple{(:first_year, :last_year), Tuple{Int64, Int64}}` - `first_year` がデータベースから利用可能な最初の年であり、`last_year` がデータベースから利用可能な最後の年である NamedTuple
