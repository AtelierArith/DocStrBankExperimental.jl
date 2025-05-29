```
sc_recycle_array_insert(rec_array, position)
```

リサイクル配列にオブジェクトを挿入します。オブジェクトは配列にコピーされません。そのためには戻り値を使用してください。

### パラメータ

  * `position`:[out] position != NULL の場合、*position は挿入されたオブジェクトの配列内の位置に設定されます。

### 戻り値

配列内のオブジェクトの新しいアドレスを返します。

### プロトタイプ

```c
void *sc_recycle_array_insert (sc_recycle_array_t * rec_array, size_t *position);
```
