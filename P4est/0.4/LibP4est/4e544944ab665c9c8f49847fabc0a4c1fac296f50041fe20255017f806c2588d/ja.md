```
sc_list_insert(list, pred, data)
```

指定されたリスト位置の後に要素を挿入します。

### パラメータ

  * `list`:[in,out] 有効なリストオブジェクト。
  * `pred`:[in,out] 挿入される要素の前の要素。
  * `data`:[in] このデータを保持する新しいリンクが作成されます。

### 戻り値

データのために作成されたリンク。

### プロトタイプ

```c
sc_link_t *sc_list_insert (sc_list_t * list, sc_link_t * pred, void *data);
```
