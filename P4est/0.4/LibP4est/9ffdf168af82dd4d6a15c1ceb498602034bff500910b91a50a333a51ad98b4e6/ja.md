```
sc_array_pqueue_add(array, temp, compar)
```

優先キューに要素を追加します。PQUEUE関数は未テストで現在無効です。この関数はビューには許可されていません。優先キューは昇順のヒープとして実装されています。ヒープは、子が親よりも小さくないバイナリツリーです。要素[0]..[elem*count-2]が有効なヒープを形成していると仮定します。その後、必要に応じてスワップすることによって[elem*count-1]を上に伝播させます。

!!! note
    配列内のすべての要素の戻り値がゼロの場合、配列は線形にソートされ、変更されません。


### パラメータ

  * `temp`:[in] 未使用の割り当てられたメモリのelem_sizeへのポインタ。
  * `compar`:[in] 使用する比較関数。

### 戻り値

スワップ操作の数を返します。

### プロトタイプ

```c
size_t sc_array_pqueue_add (sc_array_t * array, void *temp, int (*compar) (const void *, const void *));
```
