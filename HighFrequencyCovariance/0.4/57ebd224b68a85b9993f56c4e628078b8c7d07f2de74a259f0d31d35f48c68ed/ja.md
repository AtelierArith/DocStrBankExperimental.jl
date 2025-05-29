```
function SortedDataFrame(
    df::DataFrame,
    time::Symbol,
    grouping::Symbol,
    value::Symbol,
    time_period_per_unit::Dates.Period,
)

SortedDataFrame(
    df::DataFrame,
    timevar::Symbol,
    groupingvar::Symbol,
    valuevar::Symbol,
    dic::Dict{Symbol,Vector{I}},
    vol_unit::Dates.Period,
) where I<:Integer

SortedDataFrame(
    ts::SortedDataFrame{I},
    timevar::Symbol,
    groupingvar::Symbol,
    valuevar::Symbol,
    vol_unit::Dates.Period,
) where I<:Integer
```

この構造体は `DataFrame` をラップします。データフレームのコンストラクタ関数では、データを事前にソートし、グループによってデータフレームをサブセットするのが速くなるようにマッピング辞書を作成します。

コンストラクタには、データフレーム、時間列の名前、グループ化列の名前、値列の名前を渡します。

### 入力

  * `df` - ティックデータ
  * `time` - 時間を表すデータの列。
  * `grouping` - 資産名を表すデータの列。
  * `value` - 価格/対数価格/etc.を表すデータの列。
  * `time_period_per_unit` - 一単位（時間列で）の期間。

### 戻り値

  * `SortedDataFrame`。
