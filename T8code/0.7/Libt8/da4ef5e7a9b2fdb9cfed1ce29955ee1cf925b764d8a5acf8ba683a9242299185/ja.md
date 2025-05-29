```
t8_element_destroy(ts, length, elems)
```

要素の配列を解放します。

# 引数

  * `ts`:[in] クラススキームの実装。
  * `length`:[in] 配列内の要素の数。
  * `elems`:[in,out] 入力時に**length**個の割り当てられた要素ポインタの配列。出力時にはこれらのポインタはすべて解放されます。**elem**自体はこの関数によって解放されません。

### プロトタイプ

```c
void t8_element_destroy (const t8_eclass_scheme_c *ts, int length, t8_element_t **elems);
```
