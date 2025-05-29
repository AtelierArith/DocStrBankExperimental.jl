```
subset(
        data::T, 
        @nospecialize(args...)
    ) where T <: WiNDCtable
```

`args`で指定された条件に基づいて`data`のサブセットを返します。これにより、メインテーブルとセットテーブルの両方がサブセットされます。

## 必要な引数

  * `data::T`: サブセットする`WiNDCtable`。
  * `args::Tuple`: `set_name => boolean function`の形式のペア。

## 返り値

型`T`のテーブル。
