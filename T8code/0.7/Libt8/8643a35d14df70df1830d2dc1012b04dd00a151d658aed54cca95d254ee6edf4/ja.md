```
t8_element_first_descendant_face(ts, elem, face, first_desc, level)
```

指定されたレベルで、特定の面に接触する要素の最初の子孫を構築します。

# 引数

  * `ts`:[in] クラススキームの実装。
  * `elem`:[in] 入力要素。
  * `face`:[in] *elem* の面。
  * `first_desc`:[in,out] 割り当てられた要素。この要素のデータは、*face* と面を共有する *elem* の最初の子孫のデータで埋められます。
  * `level`:[in] 最初の子孫が構築されるレベル

### プロトタイプ

```c
void t8_element_first_descendant_face (const t8_eclass_scheme_c *ts, const t8_element_t *elem, int face, t8_element_t *first_desc, int level);
```
