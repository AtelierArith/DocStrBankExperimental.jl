```
log_row(vals)
```

`vals`の値に基づいて、タイプに応じたテーブル行を作成します。ログテーブルのために、`vals`の名前とタイプを[`log_header`](@ref)に渡します。内部フォーマット仕様は`SolverCore.formats`によって提供されます。

欠損値を処理するには、数値の代わりにタイプを追加します：

```
@info log_row(Any[1.0, 1])
@info log_row(Any[Float64, Int])
```

出力：

```
[ Info:  1.0e+00       1
[ Info:        -       -
```

キーワード引数：

  * `colsep::Int`: 列の間のスペースの数（デフォルト：2）
