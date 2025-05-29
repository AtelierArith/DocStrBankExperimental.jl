```
sc_array_pqueue_pop(array, result, compar)
```

優先度キューから最小の要素をポップします。PQUEUE 関数は未テストで現在無効です。この関数はビューには使用できません。この関数は、配列が昇順の有効なヒープを形成していると仮定します。

!!! note
    この関数は配列のサイズを elem_count-1 に変更します。


### パラメータ

  * `result`:[out] 未使用の割り当てられたメモリへのポインタ elem_size。
  * `compar`:[in] 使用する比較関数。

### 戻り値

スワップ操作の回数を返します。

### プロトタイプ

```c
size_t sc_array_pqueue_pop (sc_array_t * array, void *result, int (*compar) (const void *, const void *));
```
