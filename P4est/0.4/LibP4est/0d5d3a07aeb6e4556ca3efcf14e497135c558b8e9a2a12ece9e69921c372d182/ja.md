```
sc_set_abort_handler(abort_handler)
```

デフォルトのSC中止動作を制御します。

### パラメータ

  * `abort_handler`:[in] デフォルトのSC上のハンドラーを設定します (NULLは組み込みを選択します)。 ***この関数は戻ってはいけません！***

### プロトタイプ

```c
void sc_set_abort_handler (sc_abort_handler_t abort_handler);
```
