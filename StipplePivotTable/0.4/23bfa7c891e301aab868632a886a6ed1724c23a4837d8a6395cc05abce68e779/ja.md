```
pivottable(field::Symbol, args...; kwargs...)
```

指定された `field` と追加の引数を使用してピボットテーブルを作成します。

# 引数

  * `field::Symbol`: ピボットテーブルに使用されるフィールドを表すシンボル。`PivotTable` のインスタンスを参照する必要があります。
  * `args...`: `st_pivottable` 関数/コンポーネントに渡される追加の位置引数。
  * `kwargs...`: `st_pivottable` 関数/コンポーネントに渡される追加のキーワード引数。

# 戻り値

指定された構成で `st_pivottable` 関数によって作成されたピボットテーブルコンポーネントをレンダリングするためのHTML。
