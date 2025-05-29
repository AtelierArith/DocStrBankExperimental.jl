```
sc_recycle_array_remove(rec_array, position)
```

リサイクル配列からオブジェクトを削除します。これは有効でなければなりません。

### パラメータ

  * `position`:[in] 削除するオブジェクトの配列内のインデックス。

### 戻り値

削除されたオブジェクトへのポインタ。リサイクル配列に対して他の関数が呼び出されない限り、有効です。

### プロトタイプ

```c
void *sc_recycle_array_remove (sc_recycle_array_t * rec_array, size_t position);
```
