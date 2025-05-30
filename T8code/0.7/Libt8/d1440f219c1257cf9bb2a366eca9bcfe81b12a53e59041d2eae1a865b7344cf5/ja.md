```
t8_element_children_at_face(ts, elem, face, children, num_children, child_indices)
```

要素とその要素の面が与えられたとき、面に接触する要素のすべての子要素を計算します。

# 引数

  * `ts`:[in] クラススキームの実装。
  * `elem`:[in] 要素。
  * `face`:[in] *elem* の面。
  * `children`:[in,out] アロケートされた要素で、*face* と面を共有する *elem* の子要素が格納されます。子要素はその線形IDの順に格納されます。
  * `num_children`:[in] *children* の要素数。*face* に接触する子要素の数と一致する必要があります。t8*element*num*face*children
  * `child_indices`:[in,out] NULL でない場合、num*children 整数の配列が与えられ、出力ではその i 番目のエントリが i 番目の face*child の child_id になります。elem = children[0] でこの関数を呼び出すことは有効です。

### プロトタイプ

```c
void t8_element_children_at_face (const t8_eclass_scheme_c *ts, const t8_element_t *elem, int face, t8_element_t *children[], int num_children, int *child_indices);
```
