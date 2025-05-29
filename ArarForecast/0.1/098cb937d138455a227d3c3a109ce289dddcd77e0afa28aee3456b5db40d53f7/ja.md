arar(y::TimeArray, h::Int, freq::DataType, max_lag::Int)

ARARアルゴリズムを使用した予測。

予測値と予測区間の行列を返します。

# 引数

  * `y::TimeArray`: 値の列が1つだけのTimeArray。
  * `h::Int`: 整数としての予測ホライズン。
  * `freq::DataType`: DatesからのDataType、例: Dates.DayまたはDates.Month。
  * `max_lag::Int`: サンプル自己共分散の最大ラグ数を指定する整数（>= 26）。

# 例

```julia-repl
julia> arar(data, 12, Month)

```
