グレゴリオ暦の日付をその時刻の修正ユリウス日（MJD）表現に変換します。

# 引数:

  * `year::Integer` 年
  * `month::Integer` 月
  * `day::Integer` 日
  * `hour::Integer` 時
  * `minute::Integer` 分
  * `second::Real` 秒
  * `nanoseconds::Real` ナノ秒

返すもの:

  * `mjd::Float64` エポックの修正ユリウス日
