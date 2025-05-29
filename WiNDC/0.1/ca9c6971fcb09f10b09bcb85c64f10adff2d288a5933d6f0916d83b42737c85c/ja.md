```
get_subtable(data::T, subtable::String, column::Vector{Symbol}; negative::Bool = false, keep_all_columns = false) where T<:WiNDCtable

get_subtable(data::T, subtable::String; column::Symbol = :value, output::Symbol = :value, negative = false) where T<:WiNDCtable

get_subtable(data::T, subtable::Vector{String}) where T<:WiNDCtable
```

要求されたサブテーブルをDataFrameとして返します

## 必須引数

1. `data` - WiNDCtableに似たオブジェクト。
2. `subtable` - 抽出するサブテーブル名を表す文字列または文字列のベクター。

## オプション引数

  * `column` - 抽出する列を表すシンボル。デフォルトは`:value`。
  * `output` - 出力列名を表すシンボル。デフォルトは`:value`。
  * `negative` - 値を否定するかどうかを表すブール値。デフォルトは`false`。

## 戻り値

要求されたサブテーブルと列を含むDataFrameを返します。
