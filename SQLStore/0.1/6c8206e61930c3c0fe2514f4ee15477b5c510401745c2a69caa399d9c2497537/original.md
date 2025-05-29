`Rowid()` has two uses in `SQLStore`.

  * In `create_table()`: specify that a field is an `SQLite` `rowid`, that is `integer primary key`.
  * In select column definitions: specify that the table `rowid` should explicitly be included in the results. The returned rowid field is named `_rowid_`.
