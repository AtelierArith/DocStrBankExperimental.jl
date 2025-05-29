```
sc_list_remove(list, pred)
```

指定されたリスト位置の後にある要素を削除します。

### パラメータ

  * `list`:[in,out] 有効な非空リストオブジェクト。
  * `pred`:[in] 削除される要素の前の要素。*pred* == NULL の場合、最初の要素が削除され、これは [`sc_list_pop`](@ref) (list) を呼び出すことと同等です。

### 戻り値

削除されて解放されたリンクのデータ。

### プロトタイプ

```c
void *sc_list_remove (sc_list_t * list, sc_link_t * pred);
```
