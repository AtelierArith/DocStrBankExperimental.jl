```
sc_package_print_summary(log_priority)
```

SCに登録されているすべてのパッケージの概要を印刷します。デフォルトではランク0でのみ印刷される`SC_LC_GLOBAL`ログカテゴリを使用します。

### パラメータ

  * `log_priority`:[in] scログ関数に渡される優先度。

### プロトタイプ

```c
void sc_package_print_summary (int log_priority);
```
