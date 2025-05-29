```
sc_list_append(list, data)
```

リストの末尾にリスト要素を挿入します。

### パラメータ

  * `list`:[in,out] 有効なリストオブジェクト。
  * `data`:[in] このデータを保持する新しいリンクが作成されます。

### 戻り値

データのために作成されたリンク。

### プロトタイプ

```c
sc_link_t *sc_list_append (sc_list_t * list, void *data);
```
