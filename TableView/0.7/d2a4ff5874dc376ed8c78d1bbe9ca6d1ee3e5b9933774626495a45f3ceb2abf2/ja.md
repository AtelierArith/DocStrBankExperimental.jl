```
showtable(table; options::Dict{Symbol, Any} = Dict{Symbol, Any}(), option_mutator! = identity,
          dark = false, height = :auto, width = "100%", cell_changed = nothing)
```

提供された `table` を表示する `WebIO.Scope` を返します。

オプション引数:

  * `options`: agGridの `Grid` コンストラクタに直接渡されます。詳細については [documentation](https://www.ag-grid.com/documentation/) を参照してください。
  * `options_mutator!`: TableView によって populated された `options` 辞書で実行され、グリッドをカスタマイズすることができます（自己責任で – 無効なオプションを提供するとパッケージが壊れる可能性があります）。
  * `dark`: ダークテーマに切り替えます。
  * `title`: 空でない場合、テーブルの上に表示されます;
  * `height`/`width`: 出力の高さと幅を指定する CSS 属性。
  * `cell_changed`: `nothing` または `"new"`, `"old"`, `"row"`, `"col"` のフィールドを持つ単一の引数を取る関数。ユーザーがテーブルフィールドを編集するたびにこの関数が呼び出されます。すべての値は文字列になるため、必要な変換を自分で行う必要があります。
