```
t8_element_last_descendant_face(ts, elem, face, last_desc, level)
```

与えられたレベルで、指定された面に接触する要素の最後の子孫を構築します。

# 引数

  * `ts`:[in] クラススキームの実装。
  * `elem`:[in] 入力要素。
  * `face`:[in] *elem* の面。
  * `last_desc`:[in,out] 割り当てられた要素。この要素のデータは、*face* と面を共有する *elem* の最後の子孫のデータで埋められます。
  * `level`:[in] 最後の子孫が構築されるレベル

### プロトタイプ

```c
void t8_element_last_descendant_face (const t8_eclass_scheme_c *ts, const t8_element_t *elem, int face, t8_element_t *last_desc, int level);
```
