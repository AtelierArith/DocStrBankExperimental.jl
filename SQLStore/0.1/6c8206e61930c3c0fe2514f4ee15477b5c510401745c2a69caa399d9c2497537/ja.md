`Rowid()`は`SQLStore`で2つの用途があります。

  * `create_table()`内で：フィールドが`SQLite`の`rowid`、つまり`integer primary key`であることを指定します。
  * 選択列定義内で：テーブルの`rowid`を結果に明示的に含めることを指定します。返されるrowidフィールドは`_rowid_`と名付けられています。
