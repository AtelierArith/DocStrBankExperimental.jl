```
セル
```

ピボットテーブルのセルを表す可変構造体です。

# フィールド

  * `field::Union{String, Symbol}`: セルに関連付けられたフィールド。
  * `sort_by::Union{String, Symbol}`: セルがソートされる基準。デフォルトは`"label"`です。
  * `order::Union{String, Symbol}`: ソートの順序。昇順の場合は`"asc"`、降順の場合は`"desc"`を指定できます。デフォルトは`"asc"`です。
  * `label::Union{String, Symbol}`: セルのラベル。デフォルトは`field`の値です。

# コンストラクタ

  * `Cell(field::Union{String, Symbol}; kwargs...)`: 指定された`field`と、`sort_by`、`order`、`label`のオプションキーワード引数を使用して新しい`Cell`インスタンスを作成します。
