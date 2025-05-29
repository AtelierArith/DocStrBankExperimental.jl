```
get_table(data::T) where T<:WiNDCtable
```

WiNDCtableオブジェクトの主なテーブルをDataFrameとして返します

## 必要な引数

1. `data` - WiNDCtableに似たオブジェクト。

## 出力

`domain(data)`、`subtable`、および`value`の列を持つDataFrameを返します。
